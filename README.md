# rdf_mapping
sample RDF of FranceTV mapping


## Editorial Object
| Predicate | DataType | Language | Mapping (Json Path) |
| ------------- | ------------- | ------------- |------------- |
| title | xsd:string | `yes` | $.title |
| originalTitle | xsd:string | `yes` | $.original_title |
| alternativeTitle | xsd:string | `yes` | $.additional_title |
| abstract | xsd:string | `yes` | $.short_description |
| synopsis | xsd:string | `yes` | $.description |
| episodeNumber | xsd:integer |  |  |
| hasTopic | Array(Tag) |  | $.tags[*].id |
| hasGenre | Array(Category) |  | $.category[*].id |
| hasIdentifier | urn:uuid |  | $.id |
| isMemberOf | Array(Group) |  | $.groups |
| hasRelatedImage | [Media](#media) | |
| hasRelatedAudioProgramme | Array([Essence](#essence)) | | |
| hasRelatedResource | Array([Essence](#essence)) | | |

## Media
| Predicate | DataType | Language | Mapping (Json Path) |
| ------------- | ------------- | ------------- |------------- |
| resourceId | urn:uuid | | $.files[?(@.id)].id |
| locator | xsd:anyURI | | $.files[?(@.id)].url |
| dateCreated | xsd:dateTime | | $.files[?(@.id)].created_at |
| dateModified | xsd:dateTime | | $.files[?(@.id)].updated_at |
| filename | xsd:string |  | $.files[?(@.id)].filename |
| fileSize | xsd:unsignedLong |  | $.files[?(@.id)].filesize_bytes |
| hasFormat | urn:mimetype |  | $.files[?(@.id)].format.mime_type |
| height | xsd:integer | | $.files[?(@.id)].height |
| heightUnit | ftv:units | | |
| width | xsd:integer | | $.files[?(@.id)].width |
| widthUnit | ftv:units | | |
| hashValue | urn:md5:value | | $.files[?(@.id)].md5_checksum |

## Essence
| Predicate | DataType | Language | Mapping (Json Path) |
| ------------- | ------------- | ------------- |------------- |
| type | [Segmentation](#Segmentation) | | |
| dateCreated | xsd:dateTime | | $.files[?(@.id)].created_at |
| dateModified | xsd:dateTime | | $.files[?(@.id)].updated_at |
| hasPublicationEvent | Array([PublicationEvent](#publicationevent)) | | |
| frameWidth | xsd:integer | | $.files[?(@.id)].video_tracks.[0].width |
| frameWidthUnit | ftv:units | | |
| frameHeight | xsd:integer | | $.files[?(@.id)].video_tracks.[0].width |
| frameHeightUnit | ftv:units | | |
| framesPerSeconds | xsd:integer | | $.files[?(@.id)].video_tracks.[0].frame_rate_fps |

## PublicationEvent
| Predicate | DataType | Language | Mapping (Json Path) |
| ------------- | ------------- | ------------- |------------- |
| publicationEvent | [Publication](#Publication) | | |
| publicationChannel | [Chaine](#Chaine) | | |

# Codes CSA
| List |
| ---- |
| tout_public |
| 10 |
| 12 |
| 16 |
| 18 |

### Segmentation
| List |
| ---- |
| GeneriqueDebut |
| ProgrammeUtile |
| GeneriqueFin |
| BandeAnnonce |

### Publication
| List |
| ---- |
| diffusion |

### Chaine
| List |
| ---- |
| france_2 |
| france_3 |
| france_4 |
| france_5 |
| france_o |
| france_info |
| france_tv_slash |

