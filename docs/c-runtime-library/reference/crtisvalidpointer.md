---
title: _CrtIsValidPointer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
dev_langs: C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a5063a82ca90b9f854adb1ef68328272df54f4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer
驗證指標不是 null。 在 Visual Studio 2010 之前的 C 執行階段程式庫版本中，驗證指定的記憶體範圍是否可有效用於讀取和寫入 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
int _CrtIsValidPointer(   
   const void *address,  
   unsigned int size,  
   int access   
);  
```  
  
#### <a name="parameters"></a>參數  
 位址  
 要測試有效性之記憶體的開頭的指標。  
  
 `size`  
 指定之記憶體範圍的大小 (位元組)。  
  
 access  
 決定記憶體範圍的讀取/寫入存取範圍。  
  
## <a name="return-value"></a>傳回值  
 如果指定的指標不是 null，則 `_CrtIsValidPointer` 會傳回 TRUE。 在 Visual Studio 2010 之前的 C 執行階段程式庫版本中，若記憶體範圍可有效供指定的一或多個作業使用，則會傳回 TRUE。 否則，此函式會傳回 FALSE。  
  
## <a name="remarks"></a>備註  
 從 Visual Studio 2010 中的 CRT 程式庫開始，會忽略大小和存取參數，且 `_CrtIsValidPointer` 只會驗證指定的位址不是 null。 因為這項測試很容易由您自行執行，所以我們不建議您使用此函式。 在 Visual Studio 2010 之前的版本中，此函式會驗證從 `address` 開始，並延伸 `size` 個位元組之記憶體範圍，驗證其是否能有效用於指定的一或多個存取範圍作業。 當 `access` 設為 TRUE 時，會針對讀取和寫入驗證記憶體範圍。 當 `access` 設為 FALSE 時，僅會針對讀取驗證記憶體範圍。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtIsValidPointer` 的呼叫。  
  
 因為此函式會傳回 TRUE 或 FALSE，所以可將該函式傳遞至其中一個 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集，以建立簡單的偵錯處理機制。 若記憶體範圍無法有效用於讀取和寫入作業，則下列範例會引發判斷提示：  
  
```  
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );  
```  
  
 如需如何搭配其他偵錯函式和巨集使用 `_CrtIsValidPointer` 的詳細資訊，請參閱[報告巨集](/visualstudio/debugger/macros-for-reporting)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_CrtIsValidPointer`|\<crtdbg.h>|  
  
 `_CrtIsValidPointer` 是 Microsoft 擴充功能。 如需相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 請參閱 [_CrtIsValidHeapPointer](../../c-runtime-library/reference/crtisvalidheappointer.md) 主題的範例。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)