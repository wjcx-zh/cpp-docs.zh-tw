---
title: 編譯器警告 （層級 1） C4251 |Microsoft 文件
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
ms.openlocfilehash: 366d66a38685e75e47d8921f9ebd525b334ced7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4251"></a>編譯器警告 (層級 1) C4251
'identifier': 類別 'type' 必須有類別 'type2' 的用戶端所使用的 dll 介面  
  
 若要匯出的類別時，將資料損毀的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，請確認：  
  
-   所有靜態資料是透過從 DLL 匯出的函式的存取。  
  
-   沒有內嵌的方法，您的類別可以修改靜態資料。  
  
-   沒有內嵌的方法，您的類別使用 CRT 函式或其他程式庫函式使用靜態資料 (請參閱[潛在錯誤物件跨 DLL 界限傳遞 CRT](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)如需詳細資訊)。  
  
-   您的類別沒有任何方法 (不論內嵌) 可以用來使用在 EXE 和 DLL 中的具現化其中有靜態資料差異的類型。  
  
 您可以避免匯出定義的 DLL，定義虛擬函式，類別和函式您可以呼叫來具現化和刪除物件類型的類別。  然後，您就可以再呼叫虛擬函式類型上。  
  
 如需有關匯出範本的詳細資訊，請參閱[ http://support.microsoft.com/default.aspx?scid=KB;EN-US; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)。  
  
 如果您衍生自 c + + 標準程式庫、 編譯偵錯版本中的型別，可以略過 C4251 (**/MTd**) 及編譯器錯誤訊息，其中 _Container_base 是指。  
  
```  
// C4251.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251  
```