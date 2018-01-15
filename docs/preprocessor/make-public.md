---
title: "make_public |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b28c6cd71e8d8ac1165ff6e3afe95ab1f6d4de0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="makepublic"></a>make_public
表示原生類型應該具有公用組件存取範圍。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma make_public(type)  
```  
  
### <a name="parameters"></a>參數  
 `type` 是您希望具有公用組件存取範圍之類型的名稱。  
  
## <a name="remarks"></a>備註  
`make_public` 適用於您要參考的原生類型來自您無法變更之 .h 檔案時。 如果您要在具有公用組件存取範圍類型的公用函式簽章中使用原生類型，原生類型必須同時具有公用組件存取範圍，否則編譯器會發出警告。  
  
必須在全域範圍指定 `make_public`，且其有效範圍只包括宣告點開始到原始程式碼檔案的結尾。  
  
原生類型 」 可能是隱含或明確地 private，請參閱[類型可視性](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)如需詳細資訊。  
  
## <a name="example"></a>範例  
下列範例是 .h 檔案的內容，其中包含兩個原生結構的定義。  
  
```cpp  
// make_public_pragma.h  
struct Native_Struct_1 { int i; };  
struct Native_Struct_2 { int i; };  
```  
  
## <a name="example"></a>範例  
下列程式碼範例使用標頭檔，並顯示除非您使用 `make_public` 將該原生結構標記為公用，否則當在您嘗試在公開 Managed 類型中的公用函式簽章中使用該原生結構時，編譯器會產生警告。  
  
```cpp  
// make_public_pragma.cpp  
// compile with: /c /clr /W1  
#pragma warning (default : 4692)  
#include "make_public_pragma.h"  
#pragma make_public(Native_Struct_1)  
  
public ref struct A {  
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK  
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692  
};  
```  
  
## <a name="see-also"></a>請參閱  
[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)