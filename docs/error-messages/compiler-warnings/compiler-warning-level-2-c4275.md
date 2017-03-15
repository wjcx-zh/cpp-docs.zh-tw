---
title: "編譯器警告 （層級 2） C4275 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 873a96d4595b75ff6b9567500723c32d7ba5bd2b
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-2-c4275"></a>編譯器警告 (層級 2) C4275
非 DLL 介面 classkey 'identifier' 用於做為基底 DLL 介面 classkey 'identifier'  
  
 匯出的類別衍生自未匯出的類別。  
  
 若要匯出的類別時，將資料損毀的可能性降至最低[__declspec （dllexport)](../../cpp/dllexport-dllimport.md)，請確認︰  
  
-   透過從 DLL 匯出的函式來存取所有靜態資料。  
  
-   您的類別沒有內嵌的方法可以修改靜態資料。  
  
-   沒有內嵌的方法，您的類別使用 CRT 函式或其他程式庫函式會使用靜態資料。  
  
-   沒有內嵌的類別函式會使用 CRT 函式或其他程式庫函式，其中，比方說，您存取靜態資料。  
  
-   沒有類別的方法 (不管內嵌) 可以使用型別上的 EXE 和 DLL 中具現化具有靜態資料的差異。  
  
 您可以避免匯出類別所定義的 DLL，定義具有虛擬函式、 類別和函式您可以呼叫來具現化和刪除物件的型別。  然後，您就可以再呼叫虛擬函式型別上。  
  
 如需匯出範本的詳細資訊，請參閱[http://support.microsoft.com/default.aspx?scid=KB;EN-US;&16895;8](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958)。  
  
 C4275 可以忽略 Visual c + + 中，如果您衍生自 c + + 標準程式庫，編譯偵錯版本中的型別 (**/MTd**) 和 _Container_base 其中是指編譯器錯誤訊息。  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```
