---
title: _lsearch_s
ms.date: 4/2/2020
api_name:
- _lsearch_s
- _o__lsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lsearch_s
- lsearch_s
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
ms.openlocfilehash: 720b83dd48b42d77f35bce12f16e8ac79eb3b4d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341656"
---
# <a name="_lsearch_s"></a>_lsearch_s

執行值的線性搜尋。 這是 [_lsearch](lsearch.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
void *_lsearch_s(
   const void *key,
   void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的物件。

*base*<br/>
要搜尋之陣列的基底指標。

*數量*<br/>
項目數。

*大小*<br/>
每個陣列元素的大小 (以位元組為單位)。

*比較*<br/>
比較常式的指標。 第二個參數是搜尋索引鍵的指標。 第三個參數是要與索引鍵比較之陣列元素的指標。

*內容*<br/>
可能在比較函式中存取之物件的指標。

## <a name="return-value"></a>傳回值

如果找到*鍵***,_lsearch_s**返回指向*基上*與*鍵*匹配的陣列元素的指標。 如果未找到*鍵***,_lsearch_s**在陣列末尾返回指向新添加的項的指標。

如果將無效參數傳遞給函數,則調用無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,則**errno**設定為**EINVAL,** 函數傳回**NULL**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*關鍵*|*base*|*比較*|*數量*|*大小*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**空**|任意|任意|任意|任意|**埃因瓦爾**|
|任意|**空**|任意|!= 0|任意|**埃因瓦爾**|
|任意|任意|任意|任意|零|**埃因瓦爾**|
|任意|任意|**空**|an|任意|**埃因瓦爾**|

## <a name="remarks"></a>備註

**_lsearch_s**函數對*數位*元素陣列中的值*鍵*執行線性搜索,每個數位都是*寬度*位元組。 與**bsearch_s**不同 **,_lsearch_s**不需要對陣列進行排序。 如果未找到*鍵*,則 **_lsearch_s將將**數列的末尾並遞增*編號*。

*比較*函數是指向使用者提供的例程的指標,該例程比較兩個陣組元素並返回指定其關係的值。 *比較*函數還將指向上下文的指標作為第一個參數。 **_lsearch_s**調用在搜索期間*比較*一次或多次,將指標傳遞到每個調用上的兩個陣組元素。 *比較*必須比較元素,然後返回非零(表示元素不同)或 0(表示元素相同)。

如果搜索的數據結構是物件的一部分,並且*比較*函數需要訪問對象的成員,則*上下文*指標非常有用。 例如,*比較*函數中的代碼可以將 void 指標轉換為相應的物件類型並存取該物件的成員。 添加*上下文*指標使 **_lsearch_s更安全,** 因為可以使用其他上下文來避免與使用靜態變數使數據可用於*比較*函數相關的重入錯誤。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[搜尋及排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
