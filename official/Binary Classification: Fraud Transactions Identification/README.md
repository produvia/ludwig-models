# Binary Classification: Fraud Transactions Identification

<table>

<thead>

<tr>

<th>transaction_id</th>

<th>card_id</th>

<th>customer_id</th>

<th>customer_zipcode</th>

<th>merchant_id</th>

<th>merchant_name</th>

<th>merchant_category</th>

<th>merchant_zipcode</th>

<th>merchant_country</th>

<th>transaction_amount</th>

<th>authorization_response_code</th>

<th>atm_network_xid</th>

<th>cvv_2_response_xflg</th>

<th>fraud_label</th>

</tr>

</thead>

<tbody>

<tr>

<td>469483</td>

<td>9003</td>

<td>1085</td>

<td>23039</td>

<td>893</td>

<td>Wright Group</td>

<td>7917</td>

<td>91323</td>

<td>GB</td>

<td>1962</td>

<td>C</td>

<td>C</td>

<td>N</td>

<td>0</td>

</tr>

<tr>

<td>926515</td>

<td>9009</td>

<td>1001</td>

<td>32218</td>

<td>1011</td>

<td>Mums Kitchen</td>

<td>5813</td>

<td>10001</td>

<td>US</td>

<td>1643</td>

<td>C</td>

<td>D</td>

<td>M</td>

<td>1</td>

</tr>

<tr>

<td>730021</td>

<td>9064</td>

<td>1174</td>

<td>9165</td>

<td>916</td>

<td>Keller</td>

<td>7582</td>

<td>38332</td>

<td>DE</td>

<td>1184</td>

<td>D</td>

<td>B</td>

<td>M</td>

<td>0</td>

</tr>

</tbody>

</table>

## Experiment

```shell
$ ludwig experiment \
  --data_csv transactions.csv \
  --model_definition_file model_definition.yaml
```

With `model_definition.yaml`:

```yaml
$ <span class="nt">input_features</span><span class="p">:</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">customer_id</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">card_id</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">merchant_id</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">merchant_category</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">merchant_zipcode</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">transaction_amount</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">numerical</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">authorization_response_code</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">atm_network_xid</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">cvv_2_response_xflg</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">category</span>

<span class="nt">combiner</span><span class="p">:</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">concat</span>
    <span class="nt">num_fc_layers</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">1</span>
    <span class="nt">fc_size</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">48</span>

<span class="nt">output_features</span><span class="p">:</span>
  <span class="p p-Indicator">-</span>
    <span class="nt">name</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">fraud_label</span>
    <span class="nt">type</span><span class="p">:</span> <span class="l l-Scalar l-Scalar-Plain">binary</span>
```

</div>

</article>

</div>

</div>

</main>

<footer class="md-footer">

<div class="md-footer-nav">

<nav class="md-footer-nav__inner md-grid">[

<div class="md-flex__cell md-flex__cell--stretch
                  md-footer-nav__title"><span class="md-flex__ellipsis"><span class="md-footer-nav__direction">Previous</span> Getting Started</span></div>

](../getting_started/ "Getting Started")[

<div class="md-flex__cell md-flex__cell--stretch
                  md-footer-nav__title"><span class="md-flex__ellipsis"><span class="md-footer-nav__direction">Next</span> User Guide</span></div>

](../user_guide/ "User Guide")</nav>

</div>