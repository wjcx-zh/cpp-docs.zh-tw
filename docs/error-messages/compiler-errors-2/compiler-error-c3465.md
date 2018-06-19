---
title: 編譯器錯誤 C3465 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3465
dev_langs:
- C++
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1965b616ec3eb8c7de50f3a76b10e41f3579954c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254032"
---
# <a name="compiler-error-c3465"></a>編譯器錯誤 C3465
若要使用類型 'type'，您必須參考組件 'assembly'  
  
 在您重新編譯用戶端之前，類型轉送都適用於用戶端應用程式。 當您重新編譯時，您會需要每一個包含用戶端應用程式所用之類型定義之組件的參考。  
  
 如需詳細資訊，請參閱[類型轉送 (C + + /CLI)](../../windows/type-forwarding-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會建置包含類型新位置的組件。  
  
```  
// C3465.cpp  
// compile with: /clr /LD  
public ref class R {  
public:  
   ref class N {};  
};  
```  
  
## <a name="example"></a>範例  
 下列範例建置的組件，過去用於包含類型定義，現在包含類型的轉送語法。  
  
```  
// C3465_b.cpp  
// compile with: /clr /LD  
#using "C3465.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C3465。  
  
```  
// C3465_c.cpp  
// compile with: /clr  
// C3465 expected  
#using "C3465_b.dll"  
// Uncomment the following line to resolve.  
// #using "C3465.dll"  
  
int main() {  
   R^ r = gcnew R();  
}  
```