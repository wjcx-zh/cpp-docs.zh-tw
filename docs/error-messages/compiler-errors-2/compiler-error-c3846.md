---
title: 編譯器錯誤 C3846 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97d5650d1743ba379ce065d4051bfed807a1df71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268022"
---
# <a name="compiler-error-c3846"></a>編譯器錯誤 C3846
'symbol': 無法匯入來自 'assembly2' 的符號： 因為 'symbol' 已從另一個組件 'assembly1' 匯入  
  
 不能從參考組件匯符號，因為它先前從參考組件匯入。  
  
## <a name="example"></a>範例
下列範例會產生 C3846:  
  
```  
// C3846a.cpp  
// compile with: /LD /clr  
public ref struct G  
{  
};  
```  
  
 然後編譯這個：  
  
```  
// C3846b.cpp  
// compile with: /clr  
#using "c3846a.dll"  
#using "c3846a.obj"   // C3846  
  
int main()  
{  
}  
```  
