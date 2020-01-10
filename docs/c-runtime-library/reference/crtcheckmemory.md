---
title: _CrtCheckMemory
ms.date: 11/04/2016
api_name:
- _CrtCheckMemory
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
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: 7e458825a81b7032310458ccda52d9299e126a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938866"
---
# <a name="_crtcheckmemory"></a>_CrtCheckMemory

確認在偵錯堆積中配置之記憶體區塊的完整性 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>傳回值

如果成功， **_CrtCheckMemory**會傳回 TRUE;否則，函數會傳回 FALSE。

## <a name="remarks"></a>備註

**_CrtCheckMemory**函式會驗證基礎基底堆積並檢查每個記憶體區塊，藉此驗證「偵錯工具」堆積管理員所配置的記憶體。 如果在基礎基底堆積中發生錯誤或記憶體不一致的情況，則 debug 標頭資訊或覆寫緩衝區 **_CrtCheckMemory**會產生一個具有描述錯誤狀況之資訊的「偵錯工具」報告。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtCheckMemory**的呼叫。

您可以使用[_CrtSetDbgFlag](crtsetdbgflag.md)函式來設定[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)旗標的位欄位，以控制 **_CrtCheckMemory**的行為。 在每次要求記憶體配置作業時，將 **_CRTDBG_CHECK_ALWAYS_DF**位欄位轉換成會呼叫 **_CrtCheckMemory**中的結果。 雖然這個方法會降低執行速度，但會快速攔截錯誤。 關閉 **_CRTDBG_ALLOC_MEM_DF**位欄位會導致 **_CrtCheckMemory**不驗證堆積，並立即傳回**TRUE**。

因為此函式會傳回 **TRUE** 或 **FALSE**，所以可將該函式傳遞至其中一個 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 下列範例會在偵測到堆積中的損毀時造成判斷提示失敗：

```C
_ASSERTE( _CrtCheckMemory( ) );
```

如需如何搭配其他 debug 函數來使用 **_CrtCheckMemory**的詳細資訊，請參閱[堆積狀態報表](/visualstudio/debugger/crt-debug-heap-details)函式。 如需記憶體管理及偵錯堆積的概觀，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需如何使用 **_CrtCheckMemory**的範例，請參閱[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
