---
title: "編譯器錯誤 C3366 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3366
dev_langs:
- C++
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d94d3a18c02cfe81f6c3ee96635c9388f54308d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3366"></a>編譯器錯誤 C3366
'variable': 靜態資料成員的受管理或 WinRTtypes 必須定義在類別定義中  
  
 您嘗試參考的 WinRT 或 .NET 類別或介面的靜態成員不在該類別或介面的定義範圍內。  
  
 編譯器必須知道類別的完整定義 (以在一個階段後發出中繼資料) ，且需要靜態資料成員在該類別內初始化。  
  
 例如，下列範例會產生 C3366，並說明如何加以修正：  
  
```  
// C3366.cpp  
// compile with: /clr /c  
ref class X {  
   public:  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```  
