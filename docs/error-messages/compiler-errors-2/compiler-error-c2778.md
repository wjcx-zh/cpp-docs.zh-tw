---
title: 編譯器錯誤 C2778 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2778
dev_langs:
- C++
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d68180e2fc0c7c33e742f0ffdb3776baa50976f6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209709"
---
# <a name="compiler-error-c2778"></a>編譯器錯誤 C2778
__declspec 格式不正確的 GUID  
  
 不正確的 GUID 提供給[uuid](../../cpp/uuid-cpp.md)擴充的屬性。  
  
 GUID 必須是十六進位數字，以下列格式的字串：  
  
```  
// C2778a.cpp  
// compile with: /c  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};  
```  
  
 `uuid`擴充的屬性會接受字串辨識[CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring)、 使用或不含大括號分隔符號。  
  
 下列範例會產生 C2778:  
  
```  
// C2778b.cpp  
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778  
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778  
```