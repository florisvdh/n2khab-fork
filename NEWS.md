## n2khab 0.5.0 (2021-05-12)

#### Support for new data source versions

The following new data source versions are now supported by their associated reading functions:

- `habitatmap_2020` (`read_habitatmap()` - #139)
- `habitatmap_stdized_2020_v1` (`read_habitatmap_stdized()` - #139, #140)
- `habitatmap_terr_2020_v1` (`read_habitatmap_terr()` - #139, #140)
- `habitatstreams_v1.7` (`read_habitatstreams()` - #114)
- `watersurfaces_v1.1` (`read_watersurfaces()` - #118)
- `watersurfaces_hab_v4` (`read_watersurfaces_hab()` - #142)

Function documentation was updated accordingly and refined.

#### New functions

- Function `read_raster_runif()` to return the `raster_runif` data source (#136, #138)
  - The raw data source `raster_runif` is a raster with cells matching those of `GRTSmaster_habitats`.
  Their values are uniformly distributed random numbers between 0 and 1
  ([inbo/n2khab-preprocessing/pull/55](https://github.com/inbo/n2khab-preprocessing/pull/55) and following pull requests; <https://doi.org/10.5281/zenodo.4745983>).
- Function `checksum()` and associated shortcut functions to calculate file checksums (#122)

#### Other updates & internal changes

Including:

- `scheme_types` data source: updates in typegroup memberships of MNE scheme `GW_05.1_terr` (#116)
- `expand_types()` now also supports expanding `5130_hei` to `5130` (#143)


## n2khab 0.4.0 (2021-02-10)

#### New feature

- Function `read_watercourse_100mseg()` (#105) to return the `watercourse_100mseg` data source or one of its elements.
`watercourse_100mseg` is a new processed data source ([inbo/n2khab-preprocessing/pull/44](https://github.com/inbo/n2khab-preprocessing/pull/44); <https://doi.org/10.5281/zenodo.4452577>).

#### Updates & internal changes

Including:

- Update `namelist` data source: Dutch shortname of one type changed (#102).
- Drop dependency on `sp`, which was used for CRS handling in a few functions (#103).
- Minor updates in documentation and vignettes to solve newly encountered errors and notes in `R CMD check` (#107).

#### Repo and website maintenance

- Update and extend Readme (homepage) and Contributing Guide (#97, #110), including:
    - instruction for upgrading the package;
    - note on handling _proj4string_ warnings;
    - improved explanation of git workflows in developing the package.
- Continuous integration: leave Travis CI; add new GitHub Actions workflows (#108).
- Website: larger fontsize; Ubuntu Mono font for code; consistent colouring of hyperlinks (#110).

## n2khab 0.3.1 (2020-10-26)

#### Minor patch

- `read_watersurfaces()` has been limited explicitly to using data source version 'watersurfaces_v1.0'.
Accommodation of the newer 'watersurfaces_v1.1' is planned for later.

## n2khab 0.3.0 (2020-10-16)

#### Breaking change

- Functions that preprocess (non-included) N2KHAB data sources have been simplified by dropping their `path` argument (#92).
Existing R code will continue to run normally if you complied with the recommended file organization (see `vignette("v020_datastorage")` and `vignette("v022_example")`) and did not set the `path` and `file` arguments.

#### New features

- New function `read_habitatquarries()` for reading the `habitatquarries` data source (#83, #94,  [inbo/n2khab-preprocessing/pull/41](https://github.com/inbo/n2khab-preprocessing/pull/41)).
- Updates in reference lists (#88, #93, [7ce3b32](https://github.com/inbo/n2khab/commit/7ce3b32)):
    - `schemes` & `scheme_types`: updates of spatial restrictions, names and typegroup names of MNE schemes (for defining the schemes' target populations);
    - `types`: update groundwater dependency of type `2170`.

#### Internal changes

- Harden CRS representations (#84)
- Re-integrate `download_zenodo()` (from `inborutils`) (#89)
- Drop some package dependencies to speed up package loading (#89, #90)


## n2khab 0.2.0 (2020-05-08)

#### New features

- Updates in reference lists (#64, #65, #69, [e69cd52](https://github.com/inbo/n2khab/pull/73/commits/e69cd52)):
    - `types`: updates of flood dependency scores and hydrological class of several types, following several expert discussions and checks
    - `schemes` & `scheme_types`: updates regarding spatial restrictions, types and typegroup memberships of MNE schemes (for defining the schemes' target populations);
    added MHQ scheme 'HQ2120'
    - `env_pressures`: updated explanations. Each pressure now has its own explanation
    - `namelist`: according updates
- [`renv`](https://rstudio.github.io/renv) framework implemented to enhance reproducibility of generating the built-in textual data sources (#72)
- `read_env_pressures()`: an extra column '`remarks`' is now returned (#65)
- New function `read_soilmap()` for reading the `soilmap` or processed `soilmap_simple` data sources (#29; [inbo/n2khab-preprocessing/pull/34](https://github.com/inbo/n2khab-preprocessing/pull/34))
- Vignette to demonstrate package & data setup, using `read_soilmap()` as an example target (#29)
- `read_habitatsprings()` accommodates the latest version of the `habitatsprings` data source (#62, [5604002](https://github.com/inbo/n2khab/pull/73/commits/5604002))
- `read_habitatsprings()` optionally aggregates points to (population) units (#70)
- `read_habitatmap_terr()` now drops occurrences of type `7220` by default, given the information returned by `read_habitatsprings()` (#71)

Further, a number of smaller fixes and enhancements were made.

## n2khab 0.1.2 (2020-03-04)

#### Hotfix

- `read_GRTSmh()`, `read_GRTSmh_base4frac()`, `read_GRTSmh_diffres()`: avoided CRS error with more recent GDAL/PROJ.4 installations (#61)

## n2khab 0.1.1 (2020-02-26)

#### Hotfix

- `read_habitatmap_terr()`: fixed non-functioning argument `keep_aq_types=FALSE` (#60)

## n2khab 0.1.0 (2020-01-30)

#### Features of the first stable release

- Core reading and preprocessing functions
- Several built-in checklists (among which: `types` and `env_pressures`)
- Function documentation
- 4 tutorials (vignettes / articles)
- A reexport of `download_zenodo()` from `inborutils`
- Website built with `pkgdown`

#### Historical note

This package is the successor of the 'n2khabutils' package.
Previous to commit `c8608d9`, the code was part of the [n2khab-monitoring](https://github.com/inbo/n2khab-monitoring) repo (formerly 'n2khab-inputs'), where the original version history remains stored.
At that time, the package was called 'n2khabutils'.
As a convenience, the **n2khab** repo still holds the rewritten (shrinked) package history from before commit `c8608d9`, as defined by the related files and folders.
See [this](https://github.com/inbo/n2khab-monitoring/issues/28) issue in the 'n2khab-monitoring' repo, where the migration is documented.
