---
title: feupdateenv
ms.date: 04/05/2018
api_name:
- feupdateenv
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
ms.openlocfilehash: 8f40cab42e4a89b1fc5a100587b11b0e2aeeb55c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940980"
---
# <a name="feupdateenv"></a>feupdateenv

儲存目前引發的浮點例外狀況、還原指定的浮點環境狀態，然後引發儲存的浮點例外狀況。

## <a name="syntax"></a>語法

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>參數

*penv*<br/>
**Fenv_t**物件的指標，其中包含以[fegetenv](fegetenv1.md)或[feholdexcept](feholdexcept2.md)的呼叫所設定的浮點環境。 您也可以使用 FE_DFL_ENV 巨集指定預設啟動浮點環境。

## <a name="return-value"></a>傳回值

如果順利完成所有動作，則傳回 0。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Feupdateenv**函數會執行多個動作。 首先，它會將目前引發的浮點例外狀況狀態旗標儲存在自動儲存體中。 然後，它會從*penv*所指向的**fenv_t**物件中儲存的值，設定目前的浮點環境。 如果*penv*不是**FE_DFL_ENV**或不是指向有效的**fenv_t**物件，則不會定義後續的行為。 最後， **feupdateenv**會引發儲存在本機的浮點例外狀況。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|函數|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
