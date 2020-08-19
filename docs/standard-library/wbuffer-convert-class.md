---
title: wbuffer_convert 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: ba8c98075741ae6cb8db0ecdfcb1e18cf4f4f89c
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561111"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert 類別

描述資料流緩衝區，可控制與位元組資料流緩衝區之間的項目傳輸。

## <a name="syntax"></a>語法

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>參數

*Codecvt*\
[locale](../standard-library/locale-class.md) Facet，代表轉換物件。

*Elem*\
寬字元項目類型。

*性狀*\
與 *Elem* 相關聯的特性。

## <a name="remarks"></a>備註

這個類別樣板描述的資料流程緩衝區，可控制類型的專案 `_Elem` （其字元特性由類別描述 `Traits` ）與類型的位元組資料流程緩衝區之間的傳輸 `std::streambuf` 。

`Elem` 值序列與多位元組序列之間的轉換，是由類別 `Codecvt<Elem, char, std::mbstate_t>` 的物件所執行，其符合標準程式碼轉換 facet `std::codecvt<Elem, char, std::mbstate_t>` 的需求。

這個類別範本的物件會儲存：

- 其基礎位元組資料流緩衝區的指標

- 配置的轉換物件的指標 (在終結 [wbuffer_convert](../standard-library/wbuffer-convert-class.md) 物件時釋放)
