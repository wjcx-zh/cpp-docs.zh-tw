---
title: "建構輸入資料流物件 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
caps.latest.revision: 8
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7e8c664bd6632f480ba53b9dedea914bbc8e4dd7
ms.lasthandoff: 02/24/2017

---
# <a name="constructing-input-stream-objects"></a>建構輸入資料流物件
如果您只使用 `cin` 物件，就不需要建構輸入資料流。 如果您使用下列項目，就必須建構輸入資料流︰  
  
- [輸入檔案資料流建構函式](#vclrfinputfilestreamconstructorsanchor8)  
  
- [輸入字串資料流建構函式](#vclrfinputstringstreamconstructorsanchor9)  
  
##  <a name="a-namevclrfinputfilestreamconstructorsanchor8a-input-file-stream-constructors"></a><a name="vclrfinputfilestreamconstructorsanchor8"></a> 輸入檔案資料流建構函式  
 下列兩種方式可用來建立輸入檔案資料流：  
  
-   使用 `void` 引數建構函式，然後呼叫 `open` 成員函式：  
  
 ```  
    ifstream myFile; // On the stack  
    myFile.open("filename");

 
    ifstream* pmyFile = new ifstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   在建構函式引動過程中，指定檔案名稱和模式旗標，以在建構程序期間開啟檔案：  
  
 ```  
    ifstream myFile("filename");
```  
  
##  <a name="a-namevclrfinputstringstreamconstructorsanchor9a-input-string-stream-constructors"></a><a name="vclrfinputstringstreamconstructorsanchor9"></a> 輸入字串資料流建構函式  
 輸入字串資料流建構函式需要您已預先配置並初始化的儲存體位址：  
  
```  
string s("123.45");

double amt;  
istringstream myString(s);

//istringstream myString("123.45") also works  
myString>> amt; // amt contains 123.45  
```  
  
## <a name="see-also"></a>另請參閱  
 [輸入資料流](../standard-library/input-streams.md)


