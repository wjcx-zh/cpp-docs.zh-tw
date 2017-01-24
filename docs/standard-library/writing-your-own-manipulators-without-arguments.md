---
title: "撰寫不含引數的操作工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "操作工具"
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 撰寫不含引數的操作工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不使用引數的文字操作工具不需要類別對複雜巨集的衍生和用途。  假設您的印表機需要 ESC \<\>\[進入粗體的方式。  您可以插入這個對直接輸入資料流:  
  
```  
cout << "regular " << '\033' << '[' << "boldface" << endl;  
```  
  
 或者您可以定義 `bold` 操作，插入字元:  
  
```  
ostream& bold( ostream& os ) {  
    return os << '\033' << '[';  
}  
cout << "regular " << bold << "boldface" << endl;  
```  
  
 全域定義的 `bold` 函式接受 `ostream` 參考引數並傳回 `ostream` 的參考。  因為它不需要存取私用類別項目的存取，它不是成員函式或 Friend。  `bold` 函式連接至資料流，因為資料流的 `<<` 運算子多載接受該函式，使用看起來像這樣的宣告:  
  
```  
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))  
{     
   // call ios_base manipulator  
   (*_Pfn)(*(ios_base *)this);  
   return (*this);  
}  
```  
  
 您可以使用這個功能擴充其他多載運算子。  在這個案例中，是在產生的 `bold` 插入字元輸入資料流。  函式不一定會呼叫，以插入資料流時，，當相鄰字元列印時。  因此，因為資料流的緩衝區，列印可以延遲。  
  
## 請參閱  
 [輸出資料流](../standard-library/output-streams.md)