---
title: "Debugging, Tracing, and Profiling | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "debugging [.NET Framework]"
  - ".NET Framework application configuration, debugging"
  - "debugging [.NET Framework], .NET Framework application debugging"
  - "troubleshooting applications [.NET Framework], profiling"
  - "application development [.NET Framework], debugging"
  - ".NET Framework application configuration, profiling"
  - "profiling applications"
  - "troubleshooting applications [.NET Framework], debugging"
  - "troubleshooting applications [.NET Framework]"
  - "application development [.NET Framework], profiling"
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
caps.latest.revision: 28
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 28
---
# Debugging, Tracing, and Profiling
.NET Framework アプリケーションをデバッグするには、アプリケーションにデバッガーをアタッチできるようにコンパイラとランタイム環境を構成する必要があり、可能であれば、アプリケーションとそれに対応する Microsoft Intermediate Language \(MSIL\) について記号マップと行マップの両方を生成する必要があります。  マネージ アプリケーションのデバッグが完了した後は、パフォーマンスを向上するようにプロファイルできます。  プロファイルでは、最も頻繁に実行されるコードを生成するソース コード行と、そのコードの実行に要する時間を評価して記述します。  
  
 .NET Framework アプリケーションは、構成の詳細の多くを処理する Visual Studio を使用すると容易にデバッグできます。  Visual Studio がインストールされていない場合は、.NET Framework の <xref:System.Diagnostics> 名前空間に含まれるデバッグ用のクラスを使用して .NET Framework アプリケーションのパフォーマンスを確認して向上させることができます。  この名前空間には、実行フローをトレースするためのクラスとして <xref:System.Diagnostics.Trace>、<xref:System.Diagnostics.Debug>、および <xref:System.Diagnostics.TraceSource> が含まれ、コードをプロファイルするためのクラスとして <xref:System.Diagnostics.Process>、<xref:System.Diagnostics.EventLog>、および <xref:System.Diagnostics.PerformanceCounter> が含まれています。  
  
## このセクションの内容  
 [Enabling JIT\-Attach Debugging](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 .NET Framework アプリケーションにデバッグ エンジンを JIT アタッチするようにレジストリを構成する方法を示します。  
  
 [イメージのデバッグの簡略化](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 アセンブリをデバッグしやすくするために JIT 追跡を有効にし、最適化を無効にする方法を示します。  
  
 [Tracing and Instrumenting Applications](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 アプリケーションの実行中にアプリケーションの実行をモニターする方法、アプリケーションの実行が順調かどうか、何かの障害が発生しているかどうかを表示するようにアプリケーションをインストルメント化する方法について説明します。  
  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 マネージ デバッグ アシスタント \(MDA\) について説明します。これは、共通言語ランタイム \(CLR: Common Language Runtime\) と連携してランタイム状態に関する情報を提供するデバッグ支援ツールです。  
  
 [Enhancing Debugging with the Debugger Display Attributes](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 型の開発者が、その型をデバッガーで表示した場合にどのように見えるかを指定する方法について説明します。  
  
 [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 アプリケーションのパフォーマンスを追跡するために使用できるカウンターについて説明します。  
  
## 関連項目  
 [ASP.NET アプリケーションおよび AJAX アプリケーションのデバッグ](../Topic/Debugging%20ASP.NET%20and%20AJAX%20Applications.md)  
 開発時と配置後に ASP.NET アプリケーションをデバッグするための要件と手順について説明します。  
  
 [開発ガイド](../../../docs/framework/development-guide.md)  
 アプリケーションの作成、構成、デバッグ、セキュリティ、配置、および動的プログラミング、相互運用性、拡張性、メモリ管理、スレッド処理に関する情報を含む、アプリケーション開発用の主要な技術領域とタスクのすべてについての手引書です。