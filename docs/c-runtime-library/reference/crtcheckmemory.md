---
title: _CrtCheckMemory | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtCheckMemory
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
dev_langs: C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60909079a4d7c30b3a3e6c00257d882d76467585
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory
確認在偵錯堆積中配置之記憶體區塊的完整性 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## <a name="return-value"></a>傳回值  
 若成功，`_CrtCheckMemory` 會傳回 TRUE；否則此函式會傳回 FALSE。  
  
## <a name="remarks"></a>備註  
 `_CrtCheckMemory` 函式會透過確認基礎基底堆積及檢查每個記憶體區塊，來驗證偵錯堆積管理員所配置的記憶體。 如果基礎基底堆積、偵錯標頭資訊或覆寫緩衝區中發生錯誤或記憶體不一致的情況，`_CrtCheckMemory` 就會產生內含描述錯誤狀況之資訊的偵錯報告。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtCheckMemory` 的呼叫。  
  
 您可以使用 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式設定 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 旗標的位元欄位，來控制 `_CrtCheckMemory` 的行為。 開啟 **_CRTDBG_CHECK_ALWAYS_DF** 位元欄位會導致每次要求記憶體配置作業都會呼叫 `_CrtCheckMemory`。 雖然這個方法會降低執行速度，但會快速攔截錯誤。 關閉 **_CRTDBG_ALLOC_MEM_DF** 位元欄位會導致 `_CrtCheckMemory` 不確認堆積就立即傳回 **TRUE**。  
  
 因為此函式會傳回 **TRUE** 或 **FALSE**，所以可將該函式傳遞至其中一個 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 下列範例會在偵測到堆積中的損毀時造成判斷提示失敗：  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 如需如何搭配其他偵錯函式使用 `_CrtCheckMemory` 的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。 如需記憶體管理及偵錯堆積的概觀，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_CrtCheckMemory`|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 如需如何使用 `_CrtCheckMemory` 的範例，請參閱 [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9)。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)