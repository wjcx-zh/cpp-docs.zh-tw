---
title: "marshal_context::marshal_context |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a91b4f1c5f30711c46550dabb4369e380214fce1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::marshal_context
建構`marshal_context`用於 managed 和原生資料類型之間的資料轉換的物件。  
  
## <a name="syntax"></a>語法  
  
```  
marshal_context();  
```  
  
## <a name="remarks"></a>備註  
 某些資料轉換需要封送處理內容。 請參閱[概觀的封送處理 c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)如需有關哪些翻譯需要內容，且要包含在您的應用程式中的封送處理的檔案。  
  
## <a name="example"></a>範例  
 請參閱範例的[marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md)。  
  
## <a name="requirements"></a>需求  
 **標頭檔：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **命名空間：** msclr::interop  
  
## <a name="see-also"></a>請參閱  
 [C + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context 類別](../dotnet/marshal-context-class.md)