---
title: longjmp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- longjmp
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
apitype: DLLExport
f1_keywords:
- longjmp
dev_langs:
- C++
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6c26cae9a3fe83012387c93e31c4005d5614d97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="longjmp"></a>longjmp

還原堆疊環境和執行地區設定。

## <a name="syntax"></a>語法

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>參數

*env*變數中儲存的環境。

*值*值傳回至**setjmp**呼叫。

## <a name="remarks"></a>備註

**Longjmp**函式會還原先前儲存在堆疊環境和執行地區設定*env*由**setjmp**。 **setjmp**和**longjmp**提供一個方式來執行非本機**goto**; 它們通常用來執行控制項傳遞至之前所呼叫的路由，而不在錯誤處理或復原程式碼使用標準呼叫，並傳回慣例。

呼叫**setjmp**導致目前的堆疊環境儲存在*env*。 後續呼叫**longjmp**還原先前儲存的環境，並將控制權傳回給緊接著對應**setjmp**呼叫。 繼續執行如同*值*只具有所傳回**setjmp**呼叫。 常式，接收控制項可存取的所有變數 （除了暫存器變數） 的值包含這些應用程式啟動時的值**longjmp**呼叫。 無法預測暫存器變數的值。 所傳回的值**setjmp**必須為非零。 如果傳遞的 *value* 為 0，實際傳回時會以值 1 替代。

呼叫**longjmp**之前呼叫的函式**setjmp**傳回; 否則會產生無法預測結果。

使用時，請遵守下列限制**longjmp**:

- 請勿假設暫存器變數的值將保持不變。 常式的呼叫中的暫存器變數的值**setjmp**可能不會還原為適當的值之後**longjmp**執行。

- 請勿使用**longjmp**傳輸控制項從中斷處理常式，除非中斷的起因是浮點例外狀況。 在此情況下，程式可能會從透過插斷處理常式傳回**longjmp**如果它第一次重新初始化浮點數學封裝藉由呼叫 **_fpreset**。

     **請注意**使用時請小心**setjmp**和**longjmp** c + + 程式中。 因為這些函式不支援 C++ 物件語意，所以使用 C++ 例外狀況處理機制會更安全。

如需詳細資訊，請參閱[使用 setjmp/longjmp](../../cpp/using-setjmp-longjmp.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

請參閱 [_fpreset](fpreset.md) 的範例。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)<br/>
