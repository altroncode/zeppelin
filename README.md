# Zeppelin

*The package for easy configuration*

### INSTALLATION
> pip install Zeppelin

or

> poetry add Zeppelin

### USAGE

The principle of operation is based on data models
that are populated using data sources

> 💡 There are two types of data source:
> writable data source and just
> readable data source

```python
from zeppelin.data_models import base_data_model, field
from zeppelin.data_sources import data_sources


class UserSettings(base_data_model.BaseModel):
    _sections: tuple[str] = ('user',)
    
    id: str = field.Field(env='USER_ID')
    name: str = field.Field()
    is_admin: bool = field.Field()


settings = UserSettings(source=(
        data_sources.CLIArgumentsDataSource(...) + 
        data_sources.IniDataSource(...))
)
settings.name = 'John Smith'
settings.save()
```