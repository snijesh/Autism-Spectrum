


## Filtering the variants
The filters below are a good starting point provided by the Broad. You will need to experiment a little to find the values that are appropriate for your data, and to produce the tradeoff between sensitivity and specificity that is right for your analysis.

`QD < 2.0:` This is the variant confidence (from the QUAL field) divided by the unfiltered depth of non-hom-ref samples. This annotation is intended to normalize the variant quality in order to avoid inflation caused when there is deep coverage. For filtering purposes it is better to use QD than either QUAL or DP directly.

`FS > 60.0:` This is the Phred-scaled probability that there is strand bias at the site. Strand Bias tells us whether the alternate allele was seen more or less often on the forward or reverse strand than the reference allele. When there is little to no strand bias at the site, the FS value will be close to 0.

`MQ < 40.0:` This is the root mean square mapping quality over all the reads at the site. Instead of the average mapping quality of the site, this annotation gives the square root of the average of the squares of the mapping qualities at the site. It is meant to include the standard deviation of the mapping qualities. Including the standard deviation allows us to include the variation in the dataset. A low standard deviation means the values are all close to the mean, whereas a high standard deviation means the values are all far from the mean.When the mapping qualities are good at a site, the MQ will be around 60.

`SOR > 4.0:` This is another way to estimate strand bias using a test similar to the symmetric odds ratio test. SOR was created because FS tends to penalize variants that occur at the ends of exons. Reads at the ends of exons tend to only be covered by reads in one direction and FS gives those variants a bad score. SOR will take into account the ratios of reads that cover both alleles.

`MQRankSum < -8.0:` Compares the mapping qualities of the reads supporting the reference allele and the alternate allele.

`ReadPosRankSum < -8.0:` Compares whether the positions of the reference and alternate alleles are different within the reads. Seeing an allele only near the ends of reads is indicative of error, because that is where sequencers tend to make the most errors.

Learn more about [hard filtering:](https://gatk.broadinstitute.org/hc/en-us/articles/360035890471-Hard-filtering-germline-short-variants)
