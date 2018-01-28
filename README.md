# igem-data

This repository contains nearly all of the BioBrick information on [iGEM official website](http://parts.igem.org/Main_Page), including basic information, distribution information, documentations and user experiences. The data will be updated after iGEM Giant Jamboree every year.

## Structure

Each dataset is packed as a gzipped tarball, with following directory structure:

```
processed/
    <part_name>.info
    <part_name>.doc
    <part_name>.exp
    ...
```

where `<part_name>` is the identifier of each part (e.g. `BBa_B0034`).

`<part_name>.doc` and `<part_name>.exp` contain the documentation and user experiences of each part, persisted in [wikitext format](https://www.mediawiki.org/wiki/Wikitext). `<part_name>.info` contains the basic information (packed using [msgpack](https://msgpack.org/)), with a structure as below:

```javascript
{
    part_id: Number,
    part_name: String,
    part_nickname: String,
    part_results: String,
    part_type: String,
    release_statuus: String,
    sample_status: String,
    sequencing: String,
    short_desc: String,
    short_name: String,
    twins: Array of String,
    author: String,
    group: String,
    categories: Array of String,
    creation_date: String,       // YYYY-MM-DD
    distributions: Array of {    // Distribution Kits Infomation
        blast_url: String,
        distribution: String,    // Distribution Name, e.g. 'Spring 2017 Distribution'
        plasmid: String,         // e.g. 'pSB1A2'
        plate: {
            name: String,
            sequencing: String,
            well: String
        }
    },
    features: Array of {         // Features on the sequence
        id: Number,
        start: Number,
        end: Number,
        direction: String,
        type: String
    },
    parameters: Array of {
        name: String,
        units: String,
        value: String
    }
}
```
