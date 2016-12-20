---
title: "編譯器錯誤 C3707 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3707"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3707"
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3707
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : dispinterface 方法必須有 dispid  
  
 如果您使用 `dispinterface` 方法，則必須指派 `dispid` 給它。  若要修正這項錯誤，請指派 `dispid` 給 `dispinterface` 方法，例如，在下列範例中取消註解該方法的 `id` 屬性。  如需詳細資訊，請參閱屬性 [dispinterface](../../windows/dispinterface.md) 和 [id](../../windows/id.md)。  
  
 下列範例會產生 C3707：  
  
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