Python packaging ecosystem entities review
==========================================

```mermaid
graph TD;

	package_name --> requirement;
	specifier --> requirement;
	marker --> requirement;
	direct_url --> requirement;

	requirement --> distribution_metadata;
	version --> specifier;

	package_name --> pep621;
	version --> pep621;
	entry_points --> pep621;
	pep621 --> sdist;
	sdist --> wheel;
	wheel_metadata --> wheel;


	wheel_tag --> wheel_filename;
	package_name --> wheel_filename;
	version --> wheel_filename;
	wheel_filename --> wheel;

	package_name --> sdist_filename;
	version --> sdist_filename;

	marker --> wheel_tag;

	wheel_tag --> wheel_metadata;
	pep621 --> wheel_metadata;

	distribution --> installation;

	package_name --> distribution_metadata;
	version --> distribution_metadata;

	distribution_metadata --> dist-info;
	distribution_record --> dist-info;
	entry_points --> dist-info;
	wheel_metadata --> dist-info;
	direct_url --> dist-info;

	dist-info --> distribution;
	resource --> distribution;
	module_path --> distribution;

	distribution --> wheel;
	package_name --> module_path;
	module_path --> entry_points;
	sdist_manifest --> sdist;
	sdist --> sdist_archive;
	sdist_filename --> sdist_archive;

	sdist --> index;
	wheel --> index;
	entry_points --> script;

	requirement --> locator;
	locator --> index;
```

([`chart.dot`](./chart.dot) is the version for GraphViz. Unfortunately GitHub doesn't support it yet.)

For see [the glossary](./glossary.tsv) for
* the descriptions of the entities and their capabilities;
* references to PEPs where they are defined (`https://peps.python.org/pep-<pep_number>/`);
* references to PyPA documents where they are defined (`https://packaging.python.org/en/latest/specifications/<spec_name>/`).


[`compact_matrix.tsv`](./compact_matrix.tsv) shows how well different libs support various entities involved into Python packaging:
* ✅ - mostly implemented
* ⚠ - somehow implemented
* ❌ - mostly unimplemented
* ? - yet to be determined

[`full_matrix.tsv`](./full_matrix.tsv) shows the support of subfeatures in tools:
* ✅ - implemented
* ⚠ - implemented, but so poorly, that one is better to use something else
* ❌ - unimplemented
* ? - yet to be determined
