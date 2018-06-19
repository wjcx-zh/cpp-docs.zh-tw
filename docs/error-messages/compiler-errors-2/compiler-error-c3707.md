---
title: 編譯器錯誤 C3707 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7268f584d9f269b4f2f15b837379ec12ab0185d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273721"
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