# Introduction

Python IOC is a library to get the object from the configuration.

Python IOC is implemented base on the idea of Symfony Dependency Injection Component

# Usage

## Code

    container = IOC()
    container.load_file('/path/to/config.yml')
    container.load_resource('@package_name/dir/file.yml')

## Config file

    imports:
      - resource: "other-config-file.yml"
      - resource: "child-folder/config-file-2.yml"
      - resource: "@my.package.namechild-folder/config-file-2.yml"

    parameters:
      Param1: Value1
      DictParam1:
        K1: v1
        K2: v2
    
    services:
      ObjName1:
        class: my.module.class_name1
        arguments: ["%Param1%", "%DictParam1%"]
        
      ObjName2:
        class: my.module.class_name2
        arguments: [$ObjName1]