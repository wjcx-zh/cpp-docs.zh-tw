---
title: "使用 ADO.NET 進行資料存取 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework [C++], 資料存取"
  - "ADO.NET [C++]"
  - "資料 [C++], ADO.NET"
  - "資料存取 [C++], ADO.NET"
  - "資料庫 [C++], 在 C++ 中存取"
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 ADO.NET 進行資料存取 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ADO.NET 是用於資料存取的 .NET Framework API，它提供了先前資料存取方案無法匹敵的功能和簡易使用性。  本章節說明 Visual C\+\+ 使用者特有的 ADO.NET 問題，例如封送處理 \(Marshaling\) 原生型別。  
  
 ADO.NET 會在 Common Language Runtime \(CLR\) 底下執行。  因此，任何與 ADO.NET 互動的應用程式也都必須以 CLR 為目標。  不過，那並不表示原生應用程式不能使用 ADO.NET。  這些範例將會示範如何以機器碼與 ADO.NET 資料庫互動。  
  
## 在本節中  
 [如何：封送處理 ADO.NET 的 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-for-adonet-cpp-cli.md)  
  
 [如何：封送處理 ADO.NET 的 BSTR 字串](../dotnet/how-to-marshal-bstr-strings-for-adonet-cpp-cli.md)  
  
 [如何：封送處理 ADO.NET 的 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-for-adonet-cpp-cli.md)  
  
 [如何：封送處理 ADO.NET 的 VARIANT](../dotnet/how-to-marshal-a-variant-for-adonet-cpp-cli.md)  
  
 [如何：封送處理 ADO.NET 的 SAFEARRAY](../dotnet/how-to-marshal-a-safearray-for-adonet-cpp-cli.md)  
  
## 相關章節  
  
|區段|說明|  
|--------|--------|  
|[ADO.NET](../Topic/ADO.NET.md)|提供 ADO.NET 的概觀，它是公開資料存取服務給 .NET 程式設計人員的類別集合。|  
|[Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/zh-tw/5358a825-e19b-49aa-8214-674ce5fed1da)|描述如何使用 .NET 語言 \(包括 Visual C\+\+\) 建立資料庫物件 \(例如預存程序、彙總、觸發程序、使用者定義函式和使用者定義型別\)，以及如何擷取和更新 Microsoft SQL Server 2005 資料庫的資料。|  
  
## 請參閱  
 [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)