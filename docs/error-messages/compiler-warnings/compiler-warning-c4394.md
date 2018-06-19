---
title: 編譯器警告 C4394 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4394
dev_langs:
- C++
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05535621443770a2b414f1c4312efbc46e6be858
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276217"
---
# <a name="compiler-warning-c4394"></a>編譯器警告 C4394
'function': per-appdomain 符號不可使用 __declspec （dllexport） 標示  
  
 函式標示[appdomain](../../cpp/appdomain.md) `__declspec`修飾詞編譯為 MSIL （不以原生），並匯出資料表 ([匯出](../../windows/export.md)`__declspec`修飾詞) 不支援對 managed 函式。  
  
 您可以宣告 Managed 函式具有公用的存取範圍。 如需詳細資訊，請參閱[類型可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[成員可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)。  
  
 C4394 永遠視為錯誤。  您可以關閉包含此警告`#pragma warning`或 **/wd**; 請參閱[警告](../../preprocessor/warning.md)或[/w、 /W0、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd，/ /wo，我們 /Wv，/WX （警告等級）](../../build/reference/compiler-option-warning-level.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4394。  
  
```  
// C4394.cpp  
// compile with: /clr /c  
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394  
__declspec(dllexport) int g2 = 0;   // OK  
```