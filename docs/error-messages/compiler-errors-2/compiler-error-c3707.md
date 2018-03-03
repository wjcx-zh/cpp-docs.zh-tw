---
title: "編譯器錯誤 C3707 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3c61c23c093106267b4854109a8cfeb699bda78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3707"></a>編譯器錯誤 C3707
'function': dispinterface 方法必須有 dispid  
  
 如果您使用`dispinterface`方法，您必須將它指派`dispid`。 若要修正這個錯誤，可以指派`dispid`至`dispinterface`方法，例如，取消註解`id`下面範例中的方法上的屬性。 如需詳細資訊，請參閱屬性[dispinterface](../../windows/dispinterface.md)和[識別碼](../../windows/id.md)。  
  
 下列範例會產生 C3707:  
  
```  
// C3707.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(name="xx")];  
[dispinterface]  
__interface IEvents : IDispatch  
{  
   HRESULT event1([in] int i);   // C3707  
   // try the following line instead  
   // [id(1)] HRESULT event1([in] int i);  
};  
  
int main() {  
}  
```