# rdf_mapping
sample RDF of FranceTV mapping


## Editorial Object

`http://ressources.idfrancetv.fr/programmes/media#{$.id}`

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

## Image

`http://ressources.idfrancetv.fr/image/{{$.files[?(@.format.label == 'image/jpeg')].id}}`

| Predicate | DataType | Language | URI | Mapping (Json Path) |
| --------- | -------- | -------- | --- | ------------------- |
| resourceId | urn:uuid | | `yes` | $.files[?(@.id)].id |
| locator | xsd:anyURI | | `yes` | $.files[?(@.id)].url |
| dateCreated | xsd:dateTime | | | $.files[?(@.id)].created_at |
| dateModified | xsd:dateTime | | | $.files[?(@.id)].updated_at |
| filename | xsd:string | | | $.files[?(@.id)].filename |
| fileSize | xsd:unsignedLong | | | $.files[?(@.id)].filesize_bytes |
| hasFormat | urn:mimetype | | `yes` | $.files[?(@.id)].format.mime_type |
| height | xsd:integer | | | $.files[?(@.id)].height |
| heightUnit | ftv:units | | | | 
| width | xsd:integer | | | $.files[?(@.id)].width |
| widthUnit | ftv:units | | | | 
| hashValue | urn:md5 | | `yes` | $.files[?(@.id)].md5_checksum |

## Essence

`http://ressources.idfrancetv.fr/programmes/essence/{{$.files[?(@.format.label == 'video/mp4')].id}}`

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

### Categories
| List |
| ---- |
| actualites_et_societe |
| documentaires |
| enfants |
| films |
| jeux_et_divertissements |
| séries_et_fictions |
| spectacles_et_culture |
| sport |
| vie_quotidienne |
| les_videos_france_tv_slash |

###Sous-catégories
| List |
| ---- |
| emissions_culturelles |
| info_et_meteo |
| magazines_d_actu |
| politique |
| religion |
| reportages |
| sante |
| temoignages |
| animaux_et_nature |
| art_et_culture |
| environnement |
| histoire |
| politique |
| science_et_sante |
| societe |
| sport |
| voyages |
| dessins_animes |
| emissions_jeunesse_et_famille |
| films_d_animation |
| action |
| cinema_documentaire |
| comedie |
| drame |
| famille_et_enfants |

### Tags
| List |
| ---- |
| news |
| indiscretions |
| essentiels |
| bonus |
| mode_et_deco |
| primes |
| bande_annonce |
