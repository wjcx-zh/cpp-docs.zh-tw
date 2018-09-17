---
title: marshal_as |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2f57db502be6e34d275e3aba0e7705992b3c4d0d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701619"
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
*input*<br/>
[in]您想要封送處理的值`To_Type`變數。  
  
## <a name="return-value"></a>傳回值  
 類型的變數`To_Type`也就是轉換的值的`input`。  
  
## <a name="remarks"></a>備註  
 這個方法是簡化的方式，將原生和 managed 型別之間的資料轉換。 若要判斷支援哪些資料類型，請參閱[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)。 某些資料轉換需要內容。 您可以使用，以轉換這些資料型別[marshal_context 類別](../dotnet/marshal-context-class.md)。  
  
 如果您嘗試封送處理不支援的資料類型的一組`marshal_as`會產生錯誤[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)在編譯時期。 閱讀隨附此錯誤，如需詳細資訊的訊息。 `C4996`錯誤可能產生多個只是已被取代的函式。 其中一個範例就嘗試封送處理一組不支援的資料類型。  
  
 封送處理程式庫是由數個標頭檔所組成。 任何轉換必須只有一個檔案，但如果您需要為其他轉換，您可以包含其他檔案。 若要查看哪些檔案與相關聯的轉換，查詢中的資料表`Marshaling Overview`。 無論何種轉換的您想要命名空間需求也永遠有效。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [C + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_context 類別](../dotnet/marshal-context-class.md)