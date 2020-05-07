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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d8c421eb3c7a6a617ce073cbf5f36416294c1874
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920451"
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

*key*<br/>
要搜尋的物件。

*base*<br/>
要搜尋之陣列的基底指標。

*number*<br/>
項目數。

*size*<br/>
每個陣列元素的大小 (以位元組為單位)。

*何*<br/>
比較常式的指標。 第二個參數是搜尋索引鍵的指標。 第三個參數是要與索引鍵比較之陣列元素的指標。

*內容*<br/>
可能在比較函式中存取之物件的指標。

## <a name="return-value"></a>傳回值

如果找到索引*鍵*， **_lsearch_s**會傳回符合索引*鍵*之*基底*陣列元素的指標。 如果找不到索引*鍵*， **_lsearch_s**會傳回陣列結尾新增專案的指標。

如果將不正確參數傳遞至函式，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則**errno**會設定為**EINVAL** ，而函數會傳回**Null**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*key*|*base*|*何*|*number*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**Null**|任意|任意|任意|任意|**EINVAL**|
|任意|**Null**|任意|!= 0|任意|**EINVAL**|
|任意|任意|任意|任意|零|**EINVAL**|
|任意|任意|**Null**|an|任意|**EINVAL**|

## <a name="remarks"></a>備註

**_Lsearch_s**函式會在*數位*元素陣列中執行值索引*鍵*的線性搜尋，每個*寬度*為位元組。 不同于**bsearch_s**， **_lsearch_s**不需要排序陣列。 如果找不到索引*鍵*，則 **_lsearch_s**會將它新增至陣列結尾，並遞增*數位*。

*Compare*函式是使用者提供的常式指標，可比較兩個陣列元素，並傳回指定其關聯性的值。 *Compare*函數也會將內容的指標當做第一個引數。 **_lsearch_s**呼叫會*比較*搜尋期間的一或多次，並在每次呼叫時傳遞兩個陣列元素的指標。 「*比較*」必須比較元素，然後傳回非零（表示專案不同）或0（表示元素完全相同）。

如果搜尋的資料結構是物件的一部分，而且*compare*函式需要存取物件的成員，則*內容*指標可能會很有用。 例如， *compare*函數中的程式碼可以將 void 指標轉換成適當的物件類型，並存取該物件的成員。 新增*內容*指標會使 **_lsearch_s**更安全，因為可以使用額外的內容來避免與使用靜態變數相關聯的重新進入 bug，讓資料可供*compare*函數使用。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
