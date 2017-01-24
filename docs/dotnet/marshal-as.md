---
title: "marshal_as | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshal_as"
  - "msclr.interop.marshal_as"
  - "msclr::interop::marshal_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_as 樣板 [C++]"
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個方法會在原生和 Managed 環境之間轉換。  
  
## 語法  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### 參數  
 \[in\] `input`  
 要封送處理到 `To_Type` 變數的值。  
  
## 傳回值  
 為 `input`的轉換值型別 `To_Type` 的變數。  
  
## 備註  
 這個方法是轉換在原生及 Managed 資料和 Managed 型別的簡化的方式。  若要判斷哪些資料型別被支援，請參閱 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)。  有些資料轉換需要內容。  使用 [marshal\_context 類別](../dotnet/marshal-context-class.md)，您可以轉換資料型別。  
  
 如果您嘗試封送處理不支援的一組資料型別， `marshal_as` 會在編譯時期產生錯誤 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。  讀取提供給此錯誤資訊的訊息。  `C4996` 錯誤可以超過被取代的函式產生。  這個範例會嘗試封送處理不支援的一組資料型別。  
  
 封送處理程式庫包含數個標頭檔。  所有轉換只需要一個檔案，不過您可以包含其他檔案，如果您其他轉換需要。  要了解哪些轉換和哪些檔案相關，請看在 `Marshaling Overview`中的資料表。  不管您想要做什麼轉換，命名空間要求一定會生效。  
  
## 範例  
 從 `const char*` 封送處理到 `System::String` 變數型別的範例。  
  
```  
// marshal_as_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   const char* message = "Test String to Marshal";  
   String^ result;  
   result = marshal_as<String^>( message );  
   return 0;  
}  
```  
  
## 需求  
 **標頭檔:** \<msclr\\marshal.h\>、\<msclr\\ marshal\_windows.h\>、\<msclr\\ marshal\_cppstd.h\> 或 \<msclr\\ marshal\_atl.h\>  
  
 **命名空間:** msclr::interop  
  
## 請參閱  
 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_context 類別](../dotnet/marshal-context-class.md)