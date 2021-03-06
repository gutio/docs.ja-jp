---
title: "チュートリアル: デザイン時のホストされている WPF 要素のプロパティの変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "相互運用性 [WPF]"
  - "Windows フォーム, 変更 (WPF コンテンツのプロパティをデザイン時に)"
  - "WPF コンテンツ [Windows フォーム], 変更 (プロパティをデザイン時に)"
  - "WPF コンテンツ, ホスト (Windows フォームで)"
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# チュートリアル: デザイン時のホストされている WPF 要素のプロパティの変更
このチュートリアルでは、Windows フォームでホストされている Windows Presentation Foundation \(WPF\) コントロールのプロパティ値を変更する方法について説明します。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   プロジェクトを作成する。  
  
-   WPF コントロールを作成する。  
  
-   Windows フォームで WPF コントロールをホストする。  
  
-   Visual Studio の WPF デザイナーを使用してプロパティの値を変更する。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## プロジェクトの作成  
 まず、Windows フォーム プロジェクトを作成します。  
  
> [!NOTE]
>  WPF コンテンツをホストする場合は、C\# プロジェクトと Visual Basic プロジェクトのみがサポートされます。  
  
#### プロジェクトを作成するには  
  
-   `WpfHost` という名前の新しい Windows フォーム アプリケーション プロジェクトを Visual Basic または Visual C\# で作成します。  
  
## WPF コントロールの作成  
 プロジェクトに WPF コントロール型を追加したら、フォーム状に配置できます。  
  
#### WPF コントロールを作成するには  
  
1.  新しい WPF <xref:System.Windows.Controls.UserControl> をプロジェクトに追加します。  コントロール型の既定の名前である `UserControl1.xaml` を使用します。  詳細については、「[チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)」を参照してください。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `[青]` に設定します。  
  
3.  プロジェクトをビルドします。  
  
## WPF コントロールのプロパティの値を変更する  
 <xref:System.Windows.Forms.Integration.ElementHost> スマート タグにより、WPF デザイナーを使用して、ホストされている WPF の内容のプロパティを簡単に変更できます。  
  
#### WPF コントロールをホストするには  
  
1.  Windows フォーム デザイナーで `Form1` を開きます。  
  
2.  **ツールボックス** の **\[WPF ユーザー コントロール\]** タブで、`UserControl1` をダブルクリックして、フォーム上に `UserControl1` のインスタンスを作成します。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
3.  **ElementHost タスク**のスマート タグ パネルで、**\[ホストするコンテンツの編集\]** を選択します。  
  
     UserControl1.xaml が WPF デザイナーで開きます。  
  
4.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Controls.Control.Background%2A> プロパティの値を `[赤]` に設定します。  
  
5.  プロジェクトをリビルドします。  
  
6.  Windows フォーム デザイナーで `Form1` を開きます。  
  
     `UserControl1` のインスタンスが赤の背景になります。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [方法 : デザイン時にフォームの端に合わせてコントロールを配置する](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)   
 [チュートリアル : スナップ線を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)