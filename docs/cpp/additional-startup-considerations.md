---
title: "其他啟動考量 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: cb437729d2c60f15bc798438ecbbba0637bf3d22
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="additional-startup-considerations"></a>其他啟動考量
在 C++ 中，物件建構和解構可能需要執行使用者程式碼。 因此，就一定要了解哪些初始化，才能進入**主要**，哪些解構函式結束之後叫用**主要**。 (如需建構和解構物件的詳細資訊，請參閱[建構函式](../cpp/constructors-cpp.md)和[解構函式](../cpp/destructors-cpp.md)。)  
  
 下列的初始化發生之前項目以**主要**:  
  
-   靜態資料預設會初始化為零。 沒有明確初始設定式的所有靜態資料在執行其他程式碼之前會設定為零，包括執行階段初始化。 靜態資料成員仍必須明確定義。  
  
-   初始化轉譯單位中的全域靜態物件。 這可能是因為進入**主要**或之前的任何函式或物件的轉譯單位中的物件第一次使用。  
  
 **Microsoft 特定的**  
  
 Microsoft c + + 的全域靜態物件會初始化輸入之前**主要**。  
  
 **END Microsoft 特定的**  
  
 彼此互相依存，但位於不同轉譯單位中的全域靜態物件可能會產生不正確的行為。  
  
## <a name="see-also"></a>另請參閱  
 [啟動和終止](../cpp/startup-and-termination-cpp.md)
