
<!-- README.md is generated from README.Rmd. Please edit that file -->

# neurips2021\_multimodal\_topmethods

This repository is a collection of top methods submitted to the
OpenProblems / NeurIPS 2021 competition for multimodal single-cell data
integration ([link](https://openproblems.bio/neurips_2021/).

Through the pipelines and code contained in this repository, you should
be able to replicate the obtained scores for each of the top
submissions.

## Dependencies

The dependencies of this repository are the same as those of the
competition itself
([link](https://openproblems.bio/neurips_docs/submission/quickstart/#2-configure-your-local-environment)).

To run any of the methods, you need to download the required binaries
and datasets and build the relevant docker containers first.

    # download viash and nextflow
    bin/init

    # sync datasets to local
    src/sync_datasets.sh

    # build components and docker containers
    bin/viash_build --max_threads 4

You can then rerun components by running the bash script located in the
respective folders.

For example:

``` bash
$ src/predict_modality/methods/cajal/test.sh

...

N E X T F L O W  ~  version 21.04.1
Pulling openproblems-bio/neurips2021_multimodal_viash ...
Launching `openproblems-bio/neurips2021_multimodal_viash` [trusting_woese] - revision: a28e0c22c5 [1.4.0]
executor >  local (5)
[4e/f4b91d] process > get_id_predictions (4)                                                            [100%] 4 of 4, cached: 3 ✔
[94/ffca9e] process > get_id_solutions (2)                                                              [100%] 4 of 4, cached: 4 ✔
[b3/92d144] process > bind_tsv_rows:bind_tsv_rows_process (meta_metric)                                 [100%] 1 of 1, cached: 1 ✔
[44/667c85] process > mse:mse_process (openproblems_bmmc_cite_phase2_PM_gex2adt)                        [100%] 4 of 4, cached: 3 ✔
[4f/8061cc] process > correlation:correlation_process (openproblems_bmmc_cite_phase2_PM_gex2adt)        [100%] 4 of 4, cached: 3 ✔
[ea/988a0f] process > check_format:check_format_process (openproblems_bmmc_cite_phase2_PM_gex2adt)      [100%] 4 of 4, cached: 3 ✔
[dc/393dca] process > final_scores:final_scores_process (output)                                        [100%] 1 of 1 ✔

[{"method_id":"cajal","ADT2GEX":0.3273,"ATAC2GEX":0.2172,"GEX2ADT":0.4613,"GEX2ATAC":0.178,"Overall":0.2959}]
```

After the bash script has finished running, output will have been stored
in:

-   `output/pretrain/<task-id>/<method-id>/<dataset-id>.output_pretrain`:
    Pre-trained models (if required).
-   `output/predictions/<task-id>/<method-id>/<dataset-id>`: Predictions
    made by the method.
-   `output/evaluation<method-id>/<dataset-id>`: Evaluation metrics.

Where <task-id> is one of three competition tasks (`predict_modality`,
`match_modality` or `joint_embedding`).

### List of methods

| Task              | Submission    | Team               | Method name                                                                                            | Authors                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:------------------|:--------------|:-------------------|:-------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| joint\_embedding  | 170795        | Guanlab-dengkw     | [submission\_170795](src/joint_embedding/methods/submission_170795/run/config.vsh.yaml)                | John Doe <a href='https://orcid.org/0000-1111-2222-3333'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| joint\_embedding  | 170825        | Living-Systems-Lab | [submission\_170825](src/joint_embedding/methods/submission_170825/run/config.vsh.yaml)                | John Doe <a href='https://orcid.org/0000-1111-2222-3333'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| joint\_embedding  | 170936/171079 | Amateur            | [submission\_170936\_171079](src/joint_embedding/methods/submission_170936_171079/run/config.vsh.yaml) | John Doe <a href='https://orcid.org/0000-1111-2222-3333'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| match\_modality   | 169959        | GLUE               | [clue](src/match_modality/methods/clue/run/config.vsh.yaml)                                            | Zhi-Jie Cao <a href='https://orcid.org/0000-0002-0026-671X'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>, Xin-Ming Tu <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>, Chen-Rui Xia <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>                                                                                                                                                                                                             |
| predict\_modality | 170613        | Cajal              | [cajal](src/predict_modality/methods/cajal/run/config.vsh.yaml)                                        | Anna Laddach <a href='https://orcid.org/0000-0001-5552-6534'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>, Roman Laddach <a href='https://orcid.org/0000-0002-0118-4548'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>, Michael Shapiro <a href='https://orcid.org/0000-0002-2769-9320'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a> |
| predict\_modality | 169769        | Novel              | [submission\_169769](src/predict_modality/methods/submission_169769/run/config.vsh.yaml)               | John Doe <a href='https://orcid.org/0000-1111-2222-3333'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| predict\_modality | 170636        | Guanlab-dengkw     | [submission\_170636](src/predict_modality/methods/submission_170636/run/config.vsh.yaml)               | John Doe <a href='https://orcid.org/0000-1111-2222-3333'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| predict\_modality | 171123        | LS\_lab            | [submission\_171123](src/predict_modality/methods/submission_171123/run/config.vsh.yaml)               | John Doe <a href='https://orcid.org/0000-1111-2222-3333'><img src='resources/orcid_id.svg' height='16'></a> <a href='https://github.com/'><img src='resources/github_mark.svg' height='16'></a>                                                                                                                                                                                                                                                                                                                                                                                                                   |
| predict\_modality | 171129        | DSE                | [submission\_171129](src/predict_modality/methods/submission_171129/run/config.vsh.yaml)               | Hongzhi Wen, Jiayuan Ding, Wei Jin, Xiaoyan Li, Zhaoheng Li, Haoyu Han, Yuying Xie, Jiliang Tang                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |