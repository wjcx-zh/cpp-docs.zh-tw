---
title: "編譯器警告 C4439 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4439
dev_langs: C++
helpviewer_keywords: C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eec228922a6f5796587243fe2d1f2c6cc1cf6b1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4439"></a>編譯器警告 C4439
'function': 函式簽章中有 managed 類型的定義必須有 __clrcall 呼叫慣例  
  
 編譯器會隱含地取代與呼叫慣例[__clrcall](../../cpp/clrcall.md)。 若要解決這個警告，請移除`__cdecl`或`__stdcall`呼叫慣例。  
  
 C4439 永遠視為錯誤。 您可以關閉包含此警告`#pragma warning`或**/wd**; 請參閱[警告](../../preprocessor/warning.md)或[/w、 /W0、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd，/ /wo，我們 /Wv，/WX （警告等級）](../../build/reference/compiler-option-warning-level.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4439。  
  
```  
// C4439.cpp  
// compile with: /clr  
void __stdcall f( System::String^ arg ) {}   // C4439  
void __clrcall f2( System::String^ arg ) {}   // OK  
void f3( System::String^ arg ) {}   // OK  
```