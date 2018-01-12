---
title: "marshal_as |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs: C++
helpviewer_keywords: marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a209b1ee657d6ae6773ee88c64225a7dc5b4f49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="marshalas"></a>marshal_as
這個方法會將原生和 managed 環境之間的資料轉換。  
  
## <a name="syntax"></a>語法  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `input`  
 您想要封送處理的值`To_Type`變數。  
  
## <a name="return-value"></a>傳回值  
 類型的變數`To_Type`也就是轉換的值的`input`。  
  
## <a name="remarks"></a>備註  
 這個方法是一個簡化的方式將原生與 managed 型別之間的資料轉換。 若要判斷支援哪些資料型別，請參閱[概觀的封送處理 c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)。 某些資料轉換需要內容。 您可以將這些資料型別轉換使用[marshal_context 類別](../dotnet/marshal-context-class.md)。  
  
 如果您嘗試封送處理不支援的資料類型的一組`marshal_as`會產生錯誤[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)在編譯時間。 請閱讀隨附此錯誤，如需詳細資訊訊息。 `C4996`以上就已被取代的函式可能會產生錯誤。 一個範例是嘗試封送處理一對不支援的資料類型。  
  
 封送處理程式庫包含數個標頭檔。 任何轉換必須只有一個檔案，但您可以加入其他檔案，如果您需要進行其他轉換。 若要查看哪些檔案與相關聯的轉換，查詢中的資料表`Marshaling Overview`。 無論何種轉換的您想要執行，其命名空間需求是一律作用中。  
  
## <a name="example"></a>範例  
 此範例中封送處理從`const char*`至`System::String`變數型別。  
  
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
  
## <a name="requirements"></a>需求  
 **標頭檔：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **命名空間：** msclr::interop  
  
## <a name="see-also"></a>請參閱  
 [C + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_context 類別](../dotnet/marshal-context-class.md)