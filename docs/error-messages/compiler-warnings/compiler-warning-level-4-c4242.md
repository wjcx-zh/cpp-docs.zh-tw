---
title: 編譯器警告 （層級 4） C4242 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4242
dev_langs:
- C++
helpviewer_keywords:
- C4242
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 623183e5ee54c995d624f47461c724ee8f4befae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217394"
---
# <a name="compiler-warning-level-4-c4242"></a>編譯器警告 (層級 4) C4242
'identifier': 從 'type1' 轉換成 'type2'，資料可能遺失  
  
 類型不相同。 類型轉換可能會導致資料遺失。 編譯器進行類型轉換。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
 如需其他有關 C4242 的詳細資訊，請參閱[常見編譯器錯誤](/windows/desktop/WinProg64/common-compiler-errors)。  
  
 下列範例會產生 C4242:  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```