---
title: 編譯器錯誤 C2348 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2348
dev_langs:
- C++
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9728b044d05374e46b685df385409ddc3cb614f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222237"
---
# <a name="compiler-error-c2348"></a>編譯器錯誤 C2348
'type name': 不是 c-style 彙總，無法在內嵌 IDL 中匯出  
  
 要放置`struct`的.idl 檔案中[匯出](../../windows/export.md)屬性`struct`必須僅包含資料。  
  
 下列範例會產生 C2348:  
  
```  
// C2348.cpp  
// C2348 error expected  
[ module(name="SimpleMidlTest") ];  
  
[export]  
struct Point {  
   // Delete the following two lines to resolve.  
   Point() : m_i(0), m_j(0) {}  
   Point(int i, int j) : m_i(i), m_j(j) {}  
  
   int m_i;  
   int m_j;  
};  
```