---
title: "marshal_context::marshal_as | Microsoft Docs"
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
  - "marshal_context::marshal_as"
  - "marshal_context.marshal_as"
  - "msclr.interop.marshal_context.marshal_as"
  - "msclr::interop::marshal_context::marshal_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context 類別 [C++], 作業"
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_context::marshal_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在特定資料物件的封送處理對於管理資料型別和原生資料型別的轉換。  
  
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
 這個函式會在特定資料物件中封送處理。  使用這個函式只能與資料表的表示轉換成 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
 如果您嘗試封送處理不支援的一組資料型別， `marshal_as` 會在編譯時期產生錯誤 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。  讀取提供給此錯誤資訊的訊息。  `C4996` 錯誤可以超過被取代的函式產生。  會產生這個錯誤的兩個條件嘗試封送處理為不支援的一組資料型別並嘗試為需要內容的轉換使用 `marshal_as` 。  
  
 封送處理程式庫包含數個標頭檔。  所有轉換只需要一個檔案，不過您可以包含其他檔案，如果您其他轉換需要。  在封送處理檔案應該包含在每個轉換的 `Marshaling Overview in C++` 表示的資料表。  
  
## 範例  
 這個範例會建立封送處理的內容從 `System::String` 到 `const char *` 變數型別。  要轉換的資料在刪除內容的行之後不會有效。  
  
```  
// marshal_context_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   marshal_context^ context = gcnew marshal_context();  
   String^ message = gcnew String("Test String to Marshal");  
   const char* result;  
   result = context->marshal_as<const char*>( message );  
   delete context;  
   return 0;  
}  
```  
  
## 需求  
 **標頭檔:** \<msclr\\marshal.h\>、\<msclr\\ marshal\_windows.h\>、\<msclr\\ marshal\_cppstd.h\> 或 \<msclr\\ marshal\_atl.h\>  
  
 **命名空間:** msclr::interop  
  
## 請參閱  
 [C\+\+ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)   
 [marshal\_context 類別](../dotnet/marshal-context-class.md)