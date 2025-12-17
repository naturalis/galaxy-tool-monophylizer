# Monophylizer

A Galaxy tool for assessing monophyly in barcode gene trees.

## Introduction

Monophylizer is a Galaxy tool designed to assess the monophyly of species in barcode gene trees. When working with phylogenetic trees containing multiple species, each with multiple DNA barcode sequences (haplotypes), this tool evaluates whether the sequences from each species form monophyletic groups or whether they are entangled with sequences from other species.

For each species in the input tree, Monophylizer determines:
- Whether all sequences for that species are **monophyletic** (forming a single clade)
- Whether sequences are **polyphyletic** (scattered across the tree in multiple unrelated clades)
- Whether sequences are **paraphyletic** (forming a clade that also contains sequences from other species)

The tool outputs a tab-separated table containing the monophyly assessment for each species, along with information about which species they are entangled with (if any).

### Background

This tool was developed and used in a broad survey of barcode gene trees from European Lepidoptera. The survey showed that poly- and paraphyly are caused by a variety of mechanisms, including:
- The influence of various tree-building algorithms
- Misidentification of specimens
- Biological processes such as incomplete lineage sorting and introgression

As such, Monophylizer can be used both for studying evolutionary biology and for assessing data quality and analytical methods in DNA barcoding studies.

## Installation

Monophylizer is available through the Galaxy ToolShed and can be installed on any Galaxy instance.

### Installing from the ToolShed

1. Log in to your Galaxy instance as an administrator
2. Navigate to **Admin** > **Install and Uninstall** (or **Search Tool Shed**)
3. Search for "monophylizer" in the search box
4. Click on the tool and select **Install to Galaxy**
5. Choose or create a tool panel section for the tool
6. Click **Install**

The tool will be available under the selected tool panel section once installation is complete.

Alternatively, you can find the tool directly on the [Galaxy ToolShed](https://toolshed.g2.bx.psu.edu/) by searching for "monophylizer" under the owner "naturalis".

## Usage

### Input Data

**Required:**
- **Tree file**: A phylogenetic tree file containing your barcode gene tree. The tree should have multiple sequences per species, with species names included in the tip labels.
  - Supported formats: Newick, Nexus, or PhyloXML
  - Default format: Newick

**Optional:**
- **Metadata file**: A tab-separated file containing additional per-taxon metadata that will be merged into the output table

### Parameters

**Basic Options:**
- **Tree file format**: Select the format of your input tree file (Newick, Nexus, or PhyloXML)
- **Separator character**: The character that separates the taxon name from additional metadata in leaf labels (default: `|`)

**Advanced Options:**
- **Treat square brackets as opaque strings**: If enabled, square brackets in taxon names are not treated as comments (default: enabled)
- **Treat quotes as opaque strings**: If enabled, quotes in taxon names are treated as literal characters (default: enabled)
- **Treat whitespace as opaque strings**: If enabled, whitespace in taxon names is preserved (default: enabled)
- **Include subspecific epithets**: If enabled, subspecific names (trinomials) are included in the species identification (default: disabled)

### Output Data

The tool produces a **tab-separated table** with the following columns:

- **Species**: The species name extracted from the tree tip labels
- **Assessment**: The monophyly status (monophyletic, polyphyletic, or paraphyletic)
- **Tanglees**: The species that the focal species is entangled with (if any)
- **IDs**: The sequence identifiers for all tips belonging to this species
- **Metadata**: Any additional metadata from the optional metadata file

### Example Use Case

If you have a DNA barcode tree with sequences from multiple butterfly species, Monophylizer will:
1. Identify all sequences belonging to each species
2. Assess whether those sequences form a single clade
3. Report any cases where sequences from different species are intermixed
4. Provide a summary table showing the monophyly status of each species

This is particularly useful for quality control in DNA barcoding projects and for identifying potential cases of misidentification, contamination, or biological phenomena like hybridization.

## Contributing

Contributions to Monophylizer are welcome! If you would like to contribute:

1. Fork the repository
2. Create a feature branch for your changes
3. Make your modifications
4. Submit a pull request with a clear description of your changes

We appreciate bug reports, feature requests, documentation improvements, and code contributions. Please open an issue on GitHub to discuss major changes before submitting a pull request.

For development guidelines and information about testing and releases, see [DEVELOPMENT.md](DEVELOPMENT.md).

## License

This tool is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.

## Citation

If you use this tool in your research, please cite:

**Mutanen, M.**, et al., 2016. Species-level para-and polyphyly in DNA barcode gene trees: strong operational bias in European Lepidoptera. _Systematic Biology_. **65(6)**:1024-1040 doi:10.1093/sysbio/syw044
