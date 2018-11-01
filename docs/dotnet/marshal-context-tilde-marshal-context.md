---
title: marshal_context::~marshal_context
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
ms.openlocfilehash: 3bf16ab2dde4047fb845cd700821d097f733a4d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528215"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context

終結 `marshal_context` 物件。

## <a name="syntax"></a>語法

```
~marshal_context();
```

## <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 請參閱[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)如需有關何種轉譯需要內容，以及哪些封送處理的檔案必須包含在您的應用程式。

刪除 `marshal_context` 物件將會使要由該內容轉換的資料失效。 如果想要在終結 `marshal_context` 物件之後保留資料，您必須手動將資料複製至會保存的變數。

## <a name="requirements"></a>需求

**標頭檔：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >

**命名空間：** msclr::interop

## <a name="see-also"></a>另請參閱

[C++ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context 類別](../dotnet/marshal-context-class.md)