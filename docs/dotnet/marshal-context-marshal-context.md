---
title: marshal_context::marshal_context
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
ms.openlocfilehash: a1a62c47450224aa2bcacde75038adf7a8cfbb9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532583"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::marshal_context

建構`marshal_context`用於 managed 和原生資料類型之間的資料轉換的物件。

## <a name="syntax"></a>語法

```
marshal_context();
```

## <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 請參閱[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)如需有關何種轉譯需要內容，以及哪些封送處理的檔案必須包含在您的應用程式。

## <a name="example"></a>範例

範例，請參閱[marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md)。

## <a name="requirements"></a>需求

**標頭檔：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >

**命名空間：** msclr::interop

## <a name="see-also"></a>另請參閱

[C++ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context 類別](../dotnet/marshal-context-class.md)