---
title: feupdateenv | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- feupdateenv
apilocation:
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
apitype: HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f731b5a24d952c6e58341662914e185efbac1ab
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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
指標**fenv_t**物件，其中包含所設定的浮點數的環境，藉由呼叫[fegetenv](fegetenv1.md)或[feholdexcept](feholdexcept2.md)。 您也可以使用 FE_DFL_ENV 巨集指定預設啟動浮點環境。

## <a name="return-value"></a>傳回值

如果順利完成所有動作，則傳回 0。 否則，傳回非零值。

## <a name="remarks"></a>備註

**Feupdateenv**函式會執行多個動作。 首先，它會將目前引發的浮點例外狀況狀態旗標儲存在自動儲存體中。 然後，它會設定目前的浮點環境中儲存的值從**fenv_t**指向的物件*penv*。 如果*penv*不**FE_DFL_ENV**或未指向有效**fenv_t**物件，後續的行為是未定義。 最後， **feupdateenv**引發儲存在本機的浮點例外狀況。

若要使用此函式，您必須在呼叫之前使用 `#pragma fenv_access(on)` 指示詞，以關閉可能會妨礙存取的浮點最佳化作業。 如需詳細資訊，請參閱 [fenv_access](../../preprocessor/fenv-access.md)。

## <a name="requirements"></a>需求

|功能|C 標頭|C++ 標頭|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h>|\<cfenv>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
