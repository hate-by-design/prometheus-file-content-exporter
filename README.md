# Prometheus exporter for watching file content

## Forked from https://github.com/spreaker/prometheus-file-content-exporter



## How it works

You give a list to this exporter and it reads file content if file exists.  
File should include strings in following format:
key=1
next_key=2
...
It's content will be exported in metrics like:
```
file_exporter_filename{instance="file-exporter:9111",job="file-exporter",key="key"} 1
file_exporter_filename{instance="file-exporter:9111",job="file-exporter",key="next_key"} 2
```
Dockerfile included

## How to install

```
pip3 install prometheus-file-content-exporter
```

This will give you `prometheus-file-content-exporter` command line that you can run.


## How to run it

Exporter need `yaml` as configuration.  
You can specify path to config via environment variable `EXPORTER_CONFIG`.  
You can configure port on which it is exposed by environment variable `EXPORTER_PORT`


## Configuration file
In configuration file you need a list of files. Those files will be watched.  
Example:  
```yaml
# The list of file to get content from
files:
- /var/svn/main/db/current
- /tmp/test
```

## Example exporter output
```
file_content_tmp_test{file="/tmp/test"} 1123.0
```


### How to publish a new version

1. [Release new version on GitHub](https://github.com/spreaker/prometheus-file-content-exporter/releases)
2. Update version in `setup.py`
3. Run `python3 setup.py sdist upload -r pypi`

## License

This software is released under the [MIT license](LICENSE.txt).
