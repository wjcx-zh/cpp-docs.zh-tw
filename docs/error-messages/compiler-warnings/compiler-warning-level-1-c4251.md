---
title: 編譯器警告 （層級 1） C4251 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4251
dev_langs:
- C++
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d964c375adf80caef3bb5a6eb06c67ef8e3e7200
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890045"
---
# <a name="compiler-warning-level-1-c4251"></a>編譯器警告 (層級 1) C4251

'identifier': 類別 'type' 必須有 dll 介面，可供類別 'type2' 的用戶端

若要匯出的類別時，將資料損毀的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，請確認：

- 所有靜態資料是透過從 DLL 匯出的函式的存取。

- 沒有內嵌的方法，您的類別可以修改靜態資料。

- 沒有內嵌的方法，您的類別使用的 CRT 函式或其他程式庫函式會使用靜態資料 (請參閱[潛在錯誤物件跨 DLL 界限傳遞 CRT](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)如需詳細資訊)。

- 您的類別沒有任何方法 (不管內嵌) 可以用來使用 EXE 和 DLL 中的具現化其中有靜態資料差異的類型。

您可以避免匯出類別所定義的 DLL，定義具有虛擬函式，類別和函式您可以呼叫來具現化和刪除的物件類型。  然後，您就可以再呼叫虛擬函式類型。

如果您從 c + + 標準程式庫中，編譯的偵錯版本的型別衍生，就可以忽略 C4251 (**/MTd**) 和其中的編譯器錯誤訊息指的是 _Container_base。

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```