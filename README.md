# LabVIEW ORM Library

This is a LabVIEW library to provide ORM (object-relation mapping) capabilities inside of LabVIEW.
It provides the ability to map internal LabVIEW classes to database tables.

The ORM capaibilities are managed by both a class & interface cability.
The database connectivity is handled by the ADO.NET database connections, however the base functionality does NOT have a dependency on this, so it could be replaced with other database connectivity (such as the LabVIEW Database Toolkit).

This library is written for LabVIEW 2020+

## Database Support
This tool currently supports the following databases:
- PostgreSQL
- Microsoft SQL Server
- SQLite
- MySQL (limited support)
- kdb+ (limited/outdated support)

Some care has been given to support database optimized capabilities and datatyping (for instance JSON/JSONB support, or GUID support), but this is not perfect across the different interfaces.

## .NET Dependencies
The ADO.NET connection is used to support individual database interactions.  
The .NET interface used is NetStandard2.0 and the following packages are used:

(Updated 2025.02.18)
- PostgreSQL : npgsql v8.0.6
- Microsoft SQL Server : System.Data.SqlConnection (built-in)
- SQLite : System.Data.SQLite v1.0.118
- MySQL : MySqlConnecto v2.4.0
- kdb+ : KpNet

A Dapper Interface is also included, however that is not actively developed/supported/tested.

Binary Dependencies are not currently included in the repository, but are included in the VIPM package, and included as an artifact in releases

It's intended that these dependencies will be migrated to a "common" VIPM package/repo in the future, because other packages depend on them.

## .config files
The NetStandard2.0 dependency means that in some cases a .config XML file is required for development/deployment to make sure that dependencies are loaded correctly.

These files must live next to the LabVIEW Project (development), EXE/dll in deployment, and should be named in the following way:

Development: <ProjectName>.lvproj.config
Deployment: <BinaryName>.<Ext>.config

The .config files that live next to the LabVIEW project files in "BuildProjects" directory can be used as a template.


## Packed Library Support
This library is built with PPL / Common-reuse patterns in mind.  It is split between a main library and the "API" library, which wraps functions from the main library.  Only the API library is used on the palettes.

This library is distributed with PPLs (currently only for Windows).  
A .zip file with "debug" versions of the libraries is also included in the distribution.

## Library use
Please see the "ORM Full Example.vi" VI for an example of how to use the library.


## Contributing

Because of the PPL nature of this project, there are several projects for use in development.  These are located in the "BuildProjects" directory.  ** The project files in the main directory were from before PPL replacement and should not be used **

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

To contribute to this toolkit, you will need LabVIEW 2020.

## Credits

CtlReferences LabVIEW library is an open source project maintained by Viviota and licensed by the BSD 3-Clause license

## License

CtlReferences LabVIEW library is distributed under the open source BSD 3-Clause license providing everyone the right to use and distribute both souce code and compiled versions of this toolkit. See LICENSE.md file for details.