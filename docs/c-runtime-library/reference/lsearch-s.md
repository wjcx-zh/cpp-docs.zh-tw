---
title: _lsearch_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12315350b62673abb0a838f9d30830354c58da73
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404194"
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

*數字*<br/>
項目數。

*size*<br/>
每個陣列元素的大小 (以位元組為單位)。

*compare*<br/>
比較常式的指標。 第二個參數是搜尋索引鍵的指標。 第三個參數是要與索引鍵比較之陣列元素的指標。

*context*<br/>
可能在比較函式中存取之物件的指標。

## <a name="return-value"></a>傳回值

如果*金鑰*找到， **_lsearch_s**傳回的陣列元素的指標*基底*符合*金鑰*。 如果*金鑰*找不到， **_lsearch_s**傳回新加入的項目，在陣列結尾的指標。

若傳遞了無效的參數到此函式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，然後執行**errno**設**EINVAL**並傳回函式**NULL**。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>錯誤狀況

|*key*|*base*|*compare*|*數字*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|任何|任何|任何|任何|**EINVAL**|
|任何|**NULL**|任何|!= 0|任何|**EINVAL**|
|任何|任何|任何|任何|零|**EINVAL**|
|任何|任何|**NULL**|an|任何|**EINVAL**|

## <a name="remarks"></a>備註

**_Lsearch_s**函式會執行值的線性搜尋*金鑰*陣列中的*數目*項目，每個*寬度*位元組。 不同於**bsearch_s**， **_lsearch_s**不需要排序的陣列。 如果*金鑰*找不到，然後 **_lsearch_s**將它加入至陣列和遞增端*數目*。

*比較*函式是在使用者提供的常式會比較兩個陣列項目並傳回值，指定其關聯性的指標。 *比較*函式也會接受做為第一個引數的內容指標。 **_lsearch_s**呼叫*比較*在搜尋期間，將指標傳遞至兩個陣列項目，每次呼叫的一或多次。 *比較*必須比較項目，並再傳回則為非零 （表示元素為不同） 或 0 （表示項目完全相同）。

*內容*指標很有用，如果搜尋的資料結構是物件的一部分而*比較*函式需要存取物件的成員。 例如，程式碼中*比較*函式可以將 void 指標轉換成適當的物件類型，並存取成員，該物件。 新增*內容*指標可讓 **_lsearch_s**更安全，因為其他內容可用來避免重新進入 bug 將資料提供給使用靜態變數相關聯*比較*函式。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[搜尋和排序](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
