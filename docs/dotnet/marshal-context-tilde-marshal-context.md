---
title: 'marshal_context:: ~ marshal_context |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6cb7ed3c7b1ee5b28c4943d83b6a8ca6166b6d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context
終結 `marshal_context` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
~marshal_context();  
```  
  
## <a name="remarks"></a>備註  
 某些資料轉換需要封送處理內容。 請參閱[概觀的封送處理 c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)如需有關哪些翻譯需要內容，且要包含在您的應用程式中的封送處理的檔案。  
  
 刪除 `marshal_context` 物件將會使要由該內容轉換的資料失效。 如果想要在終結 `marshal_context` 物件之後保留資料，您必須手動將資料複製至會保存的變數。  
  
## <a name="requirements"></a>需求  
 **標頭檔：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **命名空間：** msclr::interop  
  
## <a name="see-also"></a>另請參閱  
 [C + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context 類別](../dotnet/marshal-context-class.md)