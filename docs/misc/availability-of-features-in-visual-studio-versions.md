---
title: "各 Visual Studio 版本的功能可用性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, 功能的可用性"
ms.assetid: cb2728da-7705-4dea-a1c3-12a0388cb652
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 各 Visual Studio 版本的功能可用性
下表顯示列出的 Visual Studio Professional 版本是否支援某些功能。  
  
-   「是」表示該 Visual Studio 版本包含該功能。  
  
-   「加入」表示該 Visual Studio 版本不包含該功能，但可以使用，您可以按一下連結，以取得詳細資訊。  
  
-   「否」表示該 Visual Studio 版本不包含該功能。  
  
||Visual Studio 2010<br /><br /> 和<br /><br /> Visual Studio 2010 SP1|[!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|  
|-|---------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
|支援的 .NET Framework 版本|2.0、3.0、3.5 SP1、4|2.0、3.0、3.5 SP1、4、4.5|2.0、3.0、3.5 SP1、4、4.5、4.5.1|  
|本機 Web 伺服器|是|是|是|  
|SQL Server Express|2008|2008|2008|  
|透過伺服器總管連接至 SQL Server 版本|2000, 2005, 2008|2000, 2005, 2008|2000, 2005, 2008|  
|ASP.NET AJAX <sup>1</sup>|是|是|是|  
|ASP.NET Model View Controller|是|是|是|  
|ASP.NET Dynamic Data|是|是|是|  
|MSBuild|是|是|是|  
|ADO.NET Entity Framework|是|是|是|  
|ADO.NET Data Services|是|是|是|  
|Microsoft Azure Tools|Add|Add||  
|智慧型裝置|否|否||  
|平行運算|是 <sup>2</sup>|是|是|  
|Windows Communication Foundation|是|是|是|  
|Windows Presentation Foundation|是|是|是|  
|.NET Rich Internet Application Services|[加入](http://go.microsoft.com/fwlink/?LinkID=230768)|是|是|  
|Silverlight 1|是|是|是|  
|Silverlight 2|否|是|是|  
|Silverlight 3|是|是|是|  
|Silverlight 4|[加入](http://go.microsoft.com/fwlink/?LinkID=153710)|是|是|  
|Silverlight 5|[加入](http://go.microsoft.com/fwlink/?LinkID=215392)，僅限 SP1。|是|是|  
|IronPython|[加入](http://go.microsoft.com/fwlink/?LinkID=183863)|[加入](http://go.microsoft.com/fwlink/?LinkID=183863)|[加入](http://go.microsoft.com/fwlink/?LinkID=183863)|  
|IronRuby|[加入](http://go.microsoft.com/fwlink/?LinkID=183864) \(英文\)|[加入](http://go.microsoft.com/fwlink/?LinkID=183864) \(英文\)|[加入](http://go.microsoft.com/fwlink/?LinkID=183864) \(英文\)|  
|Visual Studio Tools for Office|是 <sup>4</sup><br /><br /> \(Office 2007、Office 2010\)|是 <sup>4</sup> \(Office 2010\)|是 <sup>4</sup> \(Office 2013\)|  
|報表專案|是|是|是|  
|報表精靈|是|是|是|  
|Language\-Integrated Query \(LINQ\)|是|是|是|  
|SharePoint 開發|是，目標為 SharePoint 2010|是，目標為 SharePoint 2010|是，目標為 SharePoint 2013|  
|.NET Framework 4 Client Profile 支援|是|否|否|  
  
1.  ASP.NET AJAX：  
  
     伺服器端：控制項內含在 ASP.NET 3.5 中，並且已經在 Visual Studio 的 \[工具箱\] 中。  如果您使用較舊版本的 ASP.NET \(例如 ASP.NET 2.0\)，可下載 [ASP.NET AJAX 擴充功能](http://go.microsoft.com/fwlink/?LinkID=75360)。  
  
     用戶端：用戶端 ASP.NET AJAX 程式庫內含在 ASP.NET 3.5 SP1 中。  
  
2.  平行運算：  
  
     平行擴充功能包含工作平行程式庫 \(TPL\)、平行 LINQ \(PLINQ\) 及並行資料結構；這些元件內含在 .NET Framework 4 中。  原生 C\+\+ 開發的對等程式庫為並行執行階段和代理程式程式庫，其內含在 Visual Studio 2010 中。  分析工具和偵錯工具增強功能也內含在 Visual Studio 2010 中。  
  
3.  IronPython 和 IronRuby：  
  
     在 IronPython 和 IronRuby 的 CodePlex 網站上，有數個版本可使用。  請選取適用於您環境的版本。  兩種語言的最小需求都是 .NET Framework 2.0 SP1。  
  
4.  Visual Studio Tools for Office \(VSTO\) 相容性和增益集功能：  
  
    ||Visual Studio 2010|[!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]|  
    |-|------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
    |文件層級|Word 2007、Word 2010、Excel 2007、Excel 2010|Word 2010、Excel 2010|Word 2013、Excel 2013|  
    |應用程式層級|Word 2007、Word 2010、Excel 2007、Excel 2010、InfoPath 2007、InfoPath 2010、Outlook 2007、Outlook 2010、PowerPoint 2007、PowerPoint 2010、Visio 2007、Visio 2010、Project 2007、Project 2010|Word 2010、Excel 2010、InfoPath 2010、Outlook 2010、PowerPoint 2010、Visio 2010、Project 2010|Word 2013、Excel 2013、InfoPath 2013、Outlook 2013、PowerPoint 2013、Visio 2013、Project 2013|