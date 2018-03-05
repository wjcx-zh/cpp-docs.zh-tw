---
title: "明確具現化 |Microsoft 文件"
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
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e272652ecc82b65d0251194f17a746ddde58fcc1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-instantiation"></a>明確初始化
您可以使用明確具現化，建立樣板化類別或函式的具現化，而在程式碼中實際使用它。 由於當您建立使用樣板散發的程式庫 (.lib) 檔案時，這樣做很有用的，未具現化的樣板定義不會進入目的檔 (.obj)。  
  
 這個程式碼明確具現化 `MyStack` 變數和六個項目的 `int`：  
  
```cpp  
template class MyStack<int, 6>;  
```  
  
 這個陳述式建立 `MyStack` 的具現化，沒有保留物件的任何儲存區。 程式碼為所有成員產生。  
  
 下一行只明確具現化建構函式成員函式：  
  
```cpp  
template MyStack<int, 6>::MyStack( void );  
```  
  
 您可以明確具現化函式樣板中的範例所示，使用特定的型別引數來重新宣告變數，[函式樣板具現化](../cpp/function-template-instantiation.md)。  
  
 您可以使用 `extern` 關鍵字防止成員自動具現化。 例如:   
  
```cpp  
extern template class MyStack<int, 6>;  
```  
  
 同樣地，您可以將特定成員標記為外部和未具現化：  
  
```cpp  
extern template MyStack<int, 6>::MyStack( void );  
```  
  
 您可以使用 `extern` 關鍵字，防止編譯器在多個物件模組中產生相同的具現化程式碼。 如果函式被呼叫，您必須在至少一個連結模組中使用指定的明確樣板參數，來具現化樣板函式，否則當程式建立時會發生連結器錯誤。  
  
> [!NOTE]
>  在特製化的 `extern` 關鍵字只適用於類別主體之外定義的成員函式。 類別宣告內定義的函式被視為內嵌函式，永遠會具現化。  
  
## <a name="see-also"></a>請參閱  
 [函式樣板](../cpp/function-templates.md)