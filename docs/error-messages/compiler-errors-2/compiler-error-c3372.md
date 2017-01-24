---
title: "編譯器錯誤 C3372 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3372"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3372"
ms.assetid: 38ee39ed-03ff-4e6d-9104-f1977b96645d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3372
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 coclass上必須對屬性 'source' 至少指定一個介面  
  
 對於特定屬性，您必須將介面名稱傳遞為參數。  
  
 下列範例會產生 C3372：  
  
```  
// C3372.cpp #include <windows.h> [module(name="MyModule")]; [ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ] __interface IMyIface { HRESULT f1(); }; // to resolve, pass an interface name to the source attribute // for example, source(IMyIface) [ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f), source, default(IMyIface) ] // C3372 class CMyClass { }; int main() { }  
```