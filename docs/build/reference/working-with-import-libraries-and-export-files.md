---
title: "與匯入程式庫和匯出檔案一起使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "匯出檔案"
  - "匯入程式庫"
  - "匯入程式庫, 建立"
  - "LIB [C++], /DEF 選項"
  - "LIB [C++], 匯入程式庫與匯出檔案"
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 與匯入程式庫和匯出檔案一起使用
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以搭配 \/DEF 選項來使用 LIB 以建立匯入程式庫和匯出檔案。  LINK 使用匯出檔案來建置包含匯出 \(通常是一個動態連結程式庫 \(DLL\)\) 的程式，並且使用匯入程式庫來解析對其他程式中之匯出的參考。  
  
 請注意，如果您在建立 .dll 之前的預備步驟中，建立匯入程式庫，則在建置 .dll 時，必須傳遞於建置匯入程式庫時所用的同一組物件檔。  
  
 在大部分的情形下，您不需要使用 LIB 來建立您的匯入程式庫。  當您連結包含匯出的程式 \(可執行檔或 DLL\) 時，LINK 會自動建立描述匯出的匯入程式庫。  稍後當您連結參考那些匯出的程式時，您只要指定匯入程式庫。  
  
 然而，當 DLL 匯出到也是它匯入來源的程式，不論直接或間接，您必須使用 LIB 來建立其中一個匯入程式庫。  當 LIB 建立匯入程式庫，它也建立一個匯出檔案。  當連結其中一個 DLL 時，您必須使用這個匯出檔案。  
  
## 請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)