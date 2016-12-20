---
title: "MSBuild 錯誤 MSB8031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB8031"
ms.assetid: ebfaca51-fd91-4b04-8194-b4fdededd5fe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB8031
MSB8031  
  
 若要在 MFC 專案中使用 MBCS 編碼，您必須下載和安裝其他程式庫。  
  
 MFC DLL 的 MBCS 版本未包含在 Visual Studio 中，但是可以在 MFC DLL MBCS 附加元件中取得，如果您是 Visual Studio 客戶，就可以下載。  如果您沒有安裝附加元件，而嘗試建置使用 MBCS 字元集的 MFC 專案，則連結器不會尋找 DLL，並且組建會失敗。  
  
### 若要更正這個錯誤  
  
1.  從 MSDN 下載中心[下載 MBCS MFC DLL 附加元件](http://go.microsoft.com/fwlink/?LinkId=299009)，如果適合將專案轉換成 UNICODE 字元集，就這麼做。  
  
## 請參閱  
 [MFC MBCS DLL 附加元件](../mfc/mfc-mbcs-dll-add-on.md)