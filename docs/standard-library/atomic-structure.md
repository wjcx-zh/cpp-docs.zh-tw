---
title: "atomic 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: atomic/std::atomic
dev_langs: C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5525953e5f4ba68fdf1b84b02046d9ab4679abe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="atomic-structure"></a>atomic 結構
描述在 `Ty` 類型的預存值上執行不可部分完成作業的物件。  
  
## <a name="syntax"></a>語法  
  
```
template <class Ty>
struct atomic;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[atomic](http://msdn.microsoft.com/Library/a538c43f-4d48-4308-ae1b-bab1839bccb8)|建構不可部分完成物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[atomic::operator Ty 運算子](http://msdn.microsoft.com/Library/a366c700-c7a0-4bcb-8eb4-4b57dfaea065)|讀取並傳回預存值。 ([atomic:: load](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1))|  
|[atomic::operator= 運算子](http://msdn.microsoft.com/Library/fe161d57-47ae-4bad-92bf-ce32ac8d5953)|使用指定的值來取代預存值。 ([atomic:: store](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b))|  
|[atomic::operator++ 運算子](http://msdn.microsoft.com/Library/492959e9-1ea8-4e02-a031-82b1b92e91a0)|遞增預存值。 僅供整數和指標特製化使用。|  
|[atomic::operator+= 運算子](http://msdn.microsoft.com/Library/9ec97aa2-c9d7-436b-943d-2989eb2617dd)|將指定的值加入預存值。 僅供整數和指標特製化使用。|  
|[atomic::operator-- 運算子](http://msdn.microsoft.com/Library/ad7c1ea7-1f6d-4a54-bf26-07630f749864)|遞減預存值。 僅供整數和指標特製化使用。|  
|[atomic::operator-= 運算子](http://msdn.microsoft.com/Library/902d0d9f-88fd-4500-aa2d-1e50f443e77c)|將預存值減去指定的值。 僅供整數和指標特製化使用。|  
|[atomic::operator&= 運算子](http://msdn.microsoft.com/Library/90e730ac-12e1-4abb-98f5-4eadd6861a89)|對指定的值和預存值執行位元 `and`。 僅供整數特製化使用。|  
|[atomic::operator&#124;= 運算子](http://msdn.microsoft.com/Library/f105eacc-31a6-4906-abba-f1cf013599b2)|對指定的值和預存值執行位元 `or`。 僅供整數特製化使用。|  
|[atomic::operator^= 運算子](http://msdn.microsoft.com/Library/f2a4da9d-67e8-4249-9161-9998e72a33c2)|對指定的值和預存值執行位元 `exclusive or`。 僅供整數特製化使用。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[compare_exchange_strong](http://msdn.microsoft.com/Library/47bbf894-b28c-4ece-959e-67b3863cf4ed)|對 `this` 執行 `atomic_compare_and_exchange` 作業，並傳回結果。|  
|[compare_exchange_weak](http://msdn.microsoft.com/Library/e15e421a-f7a3-4272-993a-f487d2242e4f)|對 `this` 執行 `weak_atomic_compare_and_exchange` 作業，並傳回結果。|  
|[fetch_add](http://msdn.microsoft.com/Library/c68b91f2-6e8a-4ffa-8991-6bb6d466e1f3)|將指定的值加入預存值。|  
|[fetch_and](http://msdn.microsoft.com/Library/a9c83001-b72c-4085-9640-f63f866714b9)|對指定的值和預存值執行位元 `and`。|  
|[fetch_or](http://msdn.microsoft.com/Library/4c532f7f-80c5-432a-b34b-48feacab8dca)|對指定的值和預存值執行位元 `or`。|  
|[fetch_sub](http://msdn.microsoft.com/Library/8cc80d4b-0942-45a3-9db8-bbf339a903e4)|將預存值減去指定的值。|  
|[fetch_xor](http://msdn.microsoft.com/Library/92bbaff8-ee29-4a1e-aee4-d9d405285bfe)|對指定的值和預存值執行位元 `exclusive or`。|  
|[is_lock_free](http://msdn.microsoft.com/Library/b99d5130-cdda-40a2-b14c-152b13a8ba45)|指定 `this` 上的不可部分完成作業是否為「無鎖定」。 如果該類型上沒有不可部分完成作業使用鎖定，則不可部分完成類型是「無鎖定」。|  
|[載入](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1)|讀取並傳回預存值。|  
|[store](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b)|使用指定的值來取代預存值。|  
  
## <a name="remarks"></a>備註  
 `Ty` 類型必須是「完整可複製的」。 亦即，使用 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 複製其位元組一定可以產生與原始物件相等的有效 `Ty` 物件。 `compare_exchange_weak` 和 `compare_exchange_strong` 成員函式會使用 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) 來判斷兩個 `Ty` 值是否相等。 這些函式將不會使用 `Ty` 定義的 `operator==`。 `atomic` 的成員函式會使用 `memcpy` 來複製 `Ty` 類型的值。  
  
 所有指標類型都可以進行部分特製化 `atomic<Ty *>`。 特製化可以將位移加入 Managed 指標值，或從中減去位移。 算術運算會接受 `ptrdiff_t` 類型的引數，並根據 `Ty` 大小，將該引數調整為與一般位址算術一致。  
  
 每個整數類型都可以進行特製化，但 `bool` 除外。 每個特製化都會提供一組豐富的方法來進行不可部分完成算術和邏輯作業。  
  
||||  
|-|-|-|  
|`atomic<char>`|`atomic<signed char>`|`atomic<unsigned char>`|  
|`atomic<char16_t>`|`atomic<char32_t>`|`atomic<wchar_t>`|  
|`atomic<short>`|`atomic<unsigned short>`|`atomic<int>`|  
|`atomic<unsigned int>`|`atomic<long>`|`atomic<unsigned long>`|  
|`atomic<long long>`|`atomic<unsigned long long>`|  
  
 整數特製化衍生自對應的 `atomic_integral` 類型。 例如，`atomic<unsigned int>` 衍生自 `atomic_uint`。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<不可部分完成 >  
  
 **命名空間：** std  
  
## <a name="see-also"></a>請參閱  
 [\<atomic>](../standard-library/atomic.md)   
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)



