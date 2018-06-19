---
title: marshal_context 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6bf712e960cbf96ccef6c3a3e4efebdad9045818
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136990"
---
# <a name="marshalcontext-class"></a>marshal_context 類別
這個類別會在原生和 Managed 環境之間轉換。  
  
## <a name="syntax"></a>語法  
  
```  
class marshal_context  
```  
  
## <a name="remarks"></a>備註  
 為需要內容的資料轉換使用 `marshal_context` 類別。 請參閱[概觀的封送處理 c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)如需有關哪些轉換需要內容，且要包含哪一個封送處理的檔案。 在您使用內容時的封送處理結果的有效性只到 `marshal_context` 物件終結時。 若要保存結果，您必須複製資料。  
  
 相同 `marshal_context` 可用於多次的資料轉換。 重複使用內容並不會影響從先前封送處理呼叫的結果。  
  
## <a name="requirements"></a>需求  
 **標頭檔：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **命名空間：** msclr::interop  
  
## <a name="see-also"></a>另請參閱  
 [C + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)