# sample_vssolution_allproject_define
Add preprocessor constants for all Projects in Visual Studio Solution, test code

# 内容

Visual Studioソリューションに入っているすべてのプロジェクトに対して、同じプリプロセッサ定数を追加したい。

その方法を調べて成功した時のサンプルコードを残しておく。

ソリューション名「SolutionDefineTest_MessageDefine」を開いた場合は、全プロジェクトにMessageDefineというプリプロセッサ定数を定義する。それ以外のソリューション名を開いた場合は、そのプリプロセッサ定数を定義しない。

この機能を、次のようにして実現した。

1. MessageDefine.targetsファイルを作成して、C#,C++プロジェクト用の定数をそれぞれ定義し、Conditionsを使ってソリューション名の条件を付ける
1. 全プロジェクトにそのtargetsファイルをインポートする設定を追加する。次の要素をProjectに追加。 <Import Project="$(SolutionDir)\MessageDefine.targets" />

C++プロジェクトは起動直後に出るメッセージボックスのテキストを、C#プロジェクトは起動したウインドウ内のテキストを差し替えることで動作確認をした。MessageDefine定数が定義されている場合はDefineと表示され、定義されていない場合はNormalと表示される。


