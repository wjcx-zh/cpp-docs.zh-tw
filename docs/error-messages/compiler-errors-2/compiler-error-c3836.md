---
title: 編譯器錯誤 C3836 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3836
dev_langs:
- C++
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45a2eda2567e63771ed4c8919945e34ee41be1cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267390"
---
# <a name="compiler-error-c3836"></a>編譯器錯誤 C3836
靜態建構函式不可以有成員初始設定式清單  
  
 Managed 的類別不能有靜態的建構函式也有成員初始設定清單。 靜態類別建構函式會呼叫 common language runtime 不要類別初始設定，初始化靜態資料成員。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3836:  
  
```  
// C3836a.cpp  
// compile with: /clr  
ref class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```  
