---
title: "建構輸出資料流物件 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf40e6683462803fcf81a9be915a4672baefd3e9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="constructing-output-stream-objects"></a>建構輸出資料流物件
如果您只使用預先定義的 `cout`、`cerr` 或 `clog` 物件，就不需要建構輸出資料流。 您必須使用下列建構函式：  
  
- [輸出檔案資料流建構函式](#vclrfoutputfilestreamconstructorsanchor1)  
  
- [輸出字串資料流建構函式](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1"></a> 輸出檔案資料流建構函式  
 您可以使用下列兩種方式之一來建構輸出檔案資料流：  
  
-   使用預設建構函式，然後呼叫 `open` 成員函式。  
  
 ```  
    ofstream myFile; // Static or on the stack  
    myFile.open("filename");

 
    ofstream* pmyFile = new ofstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   在建構函式呼叫中，指定檔案名稱和模式旗標。  
  
 ```  
    ofstream myFile("filename", ios_base::out);
```  
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2"></a> 輸出字串資料流建構函式  
 若要建構輸出字串資料流，您可以透過下列方式使用 `ostringstream`：  
  
```  
    using namespace std;  
string sp;  
ostringstream myString;  
myString <<"this is a test" <<ends;  
sp = myString.str();
// Obtain string  
cout <<sp <endl;   
```  
  
 `ends` 操作工具即會將必要的終止 null 字元新增至字串。  
  
## <a name="see-also"></a>請參閱  
 [輸出資料流](../standard-library/output-streams.md)

