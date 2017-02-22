---
title: "明確初始化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "範本，執行個體化"
  - "明確初始化"
  - "執行個體化，明確"
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 明確初始化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用明確具現化建立樣板類別或函式的執行個體化，而不用實際在程式碼中使用它。  由於當您建立用於發行範本的程式庫 \(.lib\) 檔案是有用的，未執行個體化的樣板定義不會進入目的檔 \(.obj\)。  
  
 這個程式碼明確具現化 `int` 變數和六個項目 `MyStack` :  
  
```cpp  
template class MyStack<int, 6>;  
```  
  
 這個陳述式建立 `MyStack` 的執行個體化沒有保留物件的任何儲存區。  程式碼為所有成員產生。  
  
 下一行明確具現化只有建構函式成員函式:  
  
```cpp  
template MyStack<int, 6>::MyStack( void );  
```  
  
 如同 [函式樣板具現化](../cpp/function-template-instantiation.md)，的範例所示。您可以明確具現化的函式樣板使用特定型別引數重新宣告它們。  
  
 您可以使用 `extern` 關鍵字防止成員的自動執行個體化。  例如：  
  
```cpp  
extern template class MyStack<int, 6>;  
```  
  
 同樣地，您可以將特定成員為外部和不具現化:  
  
```cpp  
extern template MyStack<int, 6>::MyStack( void );  
```  
  
 您可以在多個物件模組可以使用 `extern` 關鍵字將會產生相同的具現化程式碼的編譯器。  如果函式被呼叫，您必須使用在至少一個已連結之模組的指定的明確樣板參數在具現化樣板函式中，否則當程式建立時會發生連結器錯誤。  
  
> [!NOTE]
>  在特製化的 `extern` 關鍵字只適用於成員函式中定義於類別的主體之外。  函式中定義於類別宣告內被視為內嵌函式和永遠執行個體化。  
  
## 請參閱  
 [函式樣板](../cpp/function-templates.md)