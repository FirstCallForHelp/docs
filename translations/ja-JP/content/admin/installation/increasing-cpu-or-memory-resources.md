---
title: CPUあるいはメモリリソースの増加
intro: '既存の {{ site.data.variables.product.prodname_ghe_server }} インスタンスに CPU またはメモリリソースを追加するには、そのインスタンスをシャットダウンし、下部の仮想プラットフォームのツールを使用して仮想マシンにリソースを割り当てます。 新たに割り当てられたリソースは起動時に自動的に認識され、追加の設定は必要ありません。'
redirect_from:
  - /enterprise/admin/installation/increasing-cpu-or-memory-resources
versions:
  enterprise-server: '*'
---

{{ site.data.reusables.enterprise_installation.warning-on-upgrading-physical-resources }}

### AWSでのCPUあるいはメモリリソースの追加

{% note %}

**ノート:** AWSでCPUあるいはメモリリソースを追加するには、EC2インスタンスを管理するためにAWSのマネージメントコンソールもしくは`aws ec2`コマンドラインインターフェースのいずれかの利用に慣れていなければなりません。 リサイズを行うための好みのAWSツールの利用の背景と詳細については、[Amazon EBS-Backed インスタンスのサイズ変更](https://docs.aws.amazon.com/ja_jp/AWSEC2/latest/UserGuide/ec2-instance-resize.html)にあるAWSのドキュメンテーションを参照してください。

{% endnote %}

#### リサイズについての考慮

{{ site.data.variables.product.product_location_enterprise }} の CPU またはメモリリソースを増加させる前に、以下のことを行ってください:
{% if currentVersion != "free-pro-team@latest" %}
- **CPU に応じてメモリーをスケーリング**
    {{ site.data.reusables.enterprise_installation.increasing-cpus-max }}{% endif %}
- **Elastic IP がインスタンスに割り当てられていることを確認**

    Elastic IP が割り当てられていない場合は、パブリック IP アドレスでの変更を考慮して、再起動後に {{ site.data.variables.product.prodname_ghe_server }} ホストの DNS A レコードを調整する必要があります。 インスタンスがVPC内で起動していれば、インスタンスが再起動してもElastic IP（EIP）は自動的に保持されます。 インスタンスがEC2-Classic内で起動されていれば、Elastic IPは手動で際割り当てが必要です。

#### サポートされているAWSインスタンスタイプ

アップグレードするインスタンスタイプは、CPU／メモリの仕様に基づいて決定しなければなりません。
{{ site.data.reusables.enterprise_installation.aws-supported-instance-types }}

#### 推奨されるAWSインスタンスタイプ

{{ site.data.reusables.enterprise_installation.aws-recommended-instance-types }}

{{ site.data.reusables.enterprise_installation.warning-on-scaling }}

#### AWSでのリサイズ

{% note %}

**ノート:**EC2-Classicで起動されたインスタンスについては、インスタンスに関連づけられたElastic IPアドレスとインスタンスIPの両方を書き留めておいてください。 インスタンスを再起動したなら、Elastic IPのアドレスを再割り当てしてください。

{% endnote %}

既存の AWS/EC2 インスタンスに CPU またはメモリリソースを追加することはできません。 その代わりに、以下を行う必要があります:

1. インスタンスを停止する。
2. インスタンスタイプを変更する。
3. インスタンスを起動します。
{{ site.data.reusables.enterprise_installation.configuration-recognized }}

### OpenStack KVMでのCPUあるいはメモリリソースの追加

既存の OpenStack KVM インスタンスに CPU またはメモリリソースを追加することはできません。 その代わりに、以下を行う必要があります:

1. 現在のインスタンスのスナップショットを取る。
2. インスタンスを停止する。
3. 希望するCPUやメモリリソースを持つ新しいインスタンスフレーバーを選択する。

### VMWareでのCPUあるいはメモリリソースの追加

{{ site.data.variables.product.product_location_enterprise }}での処理が遅いなら、CPUあるいはメモリリソースを追加する必要があるかもしれません。

{{ site.data.reusables.enterprise_installation.increasing-cpus-max }}

1. vSphere Clientを使ってVMware ESXiホストに接続してください。
2. {{ site.data.variables.product.product_location_enterprise }}をシャットダウンしてください。
3. 仮想マシンを選択し、 **Edit Settings（設定の編集）**をクリックしてください。
4. "Hardware"の下で、必要に応じて仮想マシンに割り当てられたCPUやメモリリソースを調整してください。![VMWareのセットアップリソース](/assets/images/enterprise/vmware/vsphere-hardware-tab.png)
5. 仮想マシンを起動するには、[**OK**] をクリックします。
{{ site.data.reusables.enterprise_installation.configuration-recognized }}