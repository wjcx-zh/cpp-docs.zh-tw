---
title: _CrtCheckMemory
ms.date: 11/04/2016
apiname:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: cb39a76c140934dabdd1269c02aba6018691f917
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340387"
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory

確認在偵錯堆積中配置之記憶體區塊的完整性 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>傳回值

如果成功， **_CrtCheckMemory**會傳回 TRUE; 否則此函數會傳回 FALSE。

## <a name="remarks"></a>備註

**_CrtCheckMemory**函式會驗證透過確認基礎基底堆積，並檢查每個記憶體區塊來偵錯堆積管理員所配置的記憶體。 如果基礎基底堆積、 偵錯標頭資訊或覆寫緩衝區中, 發生錯誤或記憶體不一致 **_CrtCheckMemory**描述錯誤狀況的資訊產生偵錯報表。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtCheckMemory**會在前置處理期間移除。

行為 **_CrtCheckMemory**可以控制設定的位元欄位[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)使用的旗標[_CrtSetDbgFlag](crtsetdbgflag.md)函式。 開啟 **_CRTDBG_CHECK_ALWAYS_DF**位元欄位會導致 **_CrtCheckMemory**每次要求記憶體配置作業時呼叫。 雖然這個方法會降低執行速度，但會快速攔截錯誤。 開啟 **_CRTDBG_ALLOC_MEM_DF**位元欄位會導致 **_CrtCheckMemory**不確認堆積就立即傳回至**TRUE**。

因為此函式會傳回 **TRUE** 或 **FALSE**，所以可將該函式傳遞至其中一個 [_ASSERT](assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 下列範例會在偵測到堆積中的損毀時造成判斷提示失敗：

```C
_ASSERTE( _CrtCheckMemory( ) );
```

如需有關如何 **_CrtCheckMemory**可以搭配其他偵錯函式，請參閱[Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)。 如需記憶體管理及偵錯堆積的概觀，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需如何使用的範例 **_CrtCheckMemory**，請參閱[crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
