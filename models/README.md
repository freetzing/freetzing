# freetzing models

here are the data models for freetzing (first draft)

as the old fritzing application comes with different file format
for sketches (fzz), parts (fzp) and libraries (fzb) the goal is to
change that in the new univers.

somehow we want to achieve that we have just one model for at least sketches and parts
this will open up the possibility to include them into each other.
so lets call our new model:

## freetzingBundel (fb)

```
{
  "moduleId": "unique indentifier id",
  "name": "the full name of the bundel",
  "version": "revison of the creation",
  "description": "description",
  "label": "label seen in freetzing app",
  "url": "project homepage",
  "sourceUrl": "e.g. giturl <- get the package direct from git",
  "creator": "name of the creator",
  "contributors": ["list of contributors"],
  "views": [{
      "breadboard": "source to breadboardview file (fbr)"
    },
    {
      "schematic": "source to schematicview file (fsc)"
    },
    {
      "pcb": "source to pcbview file (fpc)"
    }
  ],
  "connectors": {
    "internal": [{
      "connectorId": "moduleid+connectorid",
      "signal": "the electrical signal of the connector",
      "connected": "boolean",
      "connectedTo": [{
        "moduleId": "module id of the other fb",
        "connectorId": "connector id of the fb"
      }]
    }],
    "external": [{
      "connectorId": "external connectorid",
      "signal": "the electrical signal of the connector",
      "label": "the name in the freetzing app"
    }]
  }
}
```

## freetzing view (fv)

a view could than have a model like this
```
{
  "label": "breadboard",
  "viewid": "unique id",
  "modules": [{
    "moduleId": "fb-module id (...ref. freetzing-fb via moduleid)",
    "pos": ["x", "y"]
  }]
}
```
