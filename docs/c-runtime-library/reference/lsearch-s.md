---
title: _lsearch_s
ms.date: 11/04/2016
apiname:
- _lsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: f57a96622419e3f72fc2df5b260cbbbdd59666ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156950"
---
# <a name="lsearchs"></a>_lsearch_s

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

*key*<br/>
要搜尋的物件。

*base*<br/>
要搜尋之陣列的基底指標。

*number*<br/>
項目數。

*size*<br/>
每個陣列元素的大小 (以位元組為單位)。

*compare*<br/>
比較常式的指標。 第二個參數是搜尋索引鍵的指標。 第三個參數是要與索引鍵比較之陣列元素的指標。

*context*<br/>
可能在比較函式中存取之物件的指標。

## <a name="return-value"></a>傳回值

如果*金鑰*找到，則 **_lsearch_s**傳回的項目處之陣列的指標*基底*符合*金鑰*。 如果*金鑰*找不到， **_lsearch_s**傳回新加入的項目，在陣列結尾的指標。

若傳遞了無效的參數到此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，然後執行**errno**設為**EINVAL**和函式會傳回**NULL**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*key*|*base*|*compare*|*number*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|零|**EINVAL**|
|any|any|**NULL**|an|any|**EINVAL**|

## <a name="remarks"></a>備註

**_Lsearch_s**函式會執行值的線性搜尋*金鑰*陣列中的*號碼*項目，每個*寬度*位元組。 不同於**bsearch_s**， **_lsearch_s**不需要排序陣列。 如果*金鑰*找不到，然後 **_lsearch_s**將它新增至結尾陣列並遞增*數目*。

*比較*函式是使用者所提供的常式比較兩個陣列元素，並傳回值，指定其關聯性的指標。 *比較*函式也會做為第一個引數的內容指標。 **_lsearch_s**呼叫*比較*在搜尋期間，每次呼叫時，將指標傳遞至兩個陣列元素的一或多次。 *比較*必須比較項目，然後傳回非零 （表示元素不同） 或 0 （表示元素完全相同）。

*內容*指標適合用於搜尋的資料結構是物件的一部分並*比較*函式需要存取物件的成員。 例如，在程式碼*比較*函式可以將 void 指標轉換成適當的物件類型，並存取成員，該物件。 新增*內容*指標，會使 **_lsearch_s**更安全，因為可以使用其他的內容，以避免與使用靜態變數以將資料提供給相關聯的重新進入 bug*比較*函式。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
