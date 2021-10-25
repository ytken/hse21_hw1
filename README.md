# hse21_hw1
1. Создание символических ссылок на файлы с исходными последовательностями
```
mkdir init_data
cd init_data
 ls /usr/share/data-minor-bioinf/assembly/* | xargs -tI{} ln -s {}
```
2. Анализ загруженности сервера

3. Выбор необходимого количества чтений
```
seqtk sample -s919 oil_R1.fastq 5000000 > paired_R1.fastq
seqtk sample -s919 oil_R2.fastq 5000000 > paired_R2.fastq
seqtk sample -s919 oilMP_S4_L001_R1_001.fastq 1500000 > mate_R1.fastq
seqtk sample -s919 oilMP_S4_L001_R2_001.fastq 1500000 > mate_R2.fastq
```
Результат

4. Удалим ненужные ссылки и проведем анализ fastqc и multiqc
```
rm oil*
mkdir fastqc
ls | xargs -P 4 -tI{} fastqc -o fastqc{}
multiqc -o multiqc fastqc
```
