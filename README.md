# Monophylizer

Galaxy tool for assessing monophyly in barcode gene trees. This tool takes an input gene tree with multiple species each having multiple haplotypes and assesses the extent and nature of the entanglement of the tips. For each species, it reports whether all the tips for that species are monophyletic with respect to each other or whether they are entangled with another species and, if so, whether this is polyphyly or paraphyly. The output is a tab-separated table.

This tool was developed and used in a broad survey of barcode gene trees from European Lepidoptera. The survey showed that poly- and paraphyly are caused by a variety of mechanisms, including the influence of various tree-building algorithms, misidentification of specimens, and biological processes such as incomplete lineage sorting and introgression. As such, it can be used both for studying biology and for assessing data quality and analytical methods.

## Releasing to toolshed

How to submit a tool to the Galaxy ToolShed:

1. Create an account on the [ToolShed](https://toolshed.g2.bx.psu.edu/)
2. Create a $HOME/.planemo.yml file with the following content:

```yaml
shed_username: $USER # your ToolShed username
sheds:
  toolshed:
    key: $KEY        # your ToolShed API key, under 'User > API Keys'
    email: $EMAIL    # your ToolShed email
    password: $PASS  # your ToolShed password
```

3. Install Planemo:

```bash
pip install planemo
```

4. Validate your tool XML:

```bash
planemo lint structural_validator.xml
```

5. Test your tool:

```bash
planemo test structural_validator.xml
```

6. Publish your tool:

```bash
planemo shed_create --shed_target toolshed
```

7. Update your tool:

```bash
planemo shed_update --shed_target toolshed
```

## Citation

If you use this tool, please cite:

**Marko, M.**, et al., 2016. Species-level para-and polyphyly in DNA barcode gene trees: strong operational bias in European Lepidoptera. _Systematic Biology_. **65(6)**:1024-1040 doi:10.1093/sysbio/syw044
