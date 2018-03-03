---
title: "編譯器錯誤 C3372 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3372
dev_langs:
- C++
helpviewer_keywords:
- C3372
ms.assetid: 38ee39ed-03ff-4e6d-9104-f1977b96645d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a2a9a576db2727efc6b67d5467d6a9c9b8d889f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3372"></a>編譯器錯誤 C3372
在 coclass上必須對屬性 'source' 至少指定一個介面  
  
 對於特定屬性，您必須將介面名稱傳遞為參數。  
  
 下列範例會產生 C3372：  
  
```  
// C3372.cpp  
#include <windows.h>  
[module(name="MyModule")];  
  
[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]  
__interface IMyIface {  
   HRESULT f1();  
};  
// to resolve, pass an interface name to the source attribute  
// for example, source(IMyIface)  
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f), source,   
  default(IMyIface) ] // C3372  
class CMyClass {  
};  
  
int main() {  
}  
```