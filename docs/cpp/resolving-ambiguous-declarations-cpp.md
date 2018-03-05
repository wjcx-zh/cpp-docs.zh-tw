---
title: "解析模稜兩可的宣告 （c + +） |Microsoft 文件"
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
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 70c010cf3806581c6b77bb508f3adb68e3c230f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resolving-ambiguous-declarations-c"></a>解析模稜兩可的宣告 （c + +）
若要從一個類型明確轉換成另一個類型，您必須使用轉型來指定所需的類型名稱。 某些類型轉換會導致語意模稜兩可的情況。 下列函式樣式類型轉換就是模稜兩可的情況：  
  
```  
char *aName( String( s ) );  
```  
  
 不清楚是否函式宣告或物件宣告的函式樣式轉換為初始設定式： 它可以宣告函式傳回型別**char \*** 採用一個引數的型別`String`它可以宣告物件`aName`並初始化其值為`s`要轉型為型別`String`。  
  
 如果宣告可以視為有效的函式宣告，則會以此方式處理。 只有在不可能是函式宣告的情況下 (也就是它的語意不正確)，才會查看陳述式是否為函式樣式類型轉換。 因此，編譯器會將陳述式視為函式宣告，必且忽略識別項 `s` 前後的括號。 換句話說，陳述式：  
  
```  
char *aName( (String)s );  
```  
  
 和  
  
```  
char *aName = String( s );  
```  
  
 是很明確宣告的物件和使用者定義從類型轉換`String`輸入**char \*** 叫用以執行的初始化`aName`。  
  
## <a name="see-also"></a>請參閱  
 