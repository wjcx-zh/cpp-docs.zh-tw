---
title: ctype&lt;char&gt; 類別
ms.date: 11/04/2016
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
ms.openlocfilehash: d2c74ef46babe388cfa6d649e8b4501b7c235bb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220960"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; 類別

類別是類別樣板的明確特製化 `ctype\<CharType>` ，可做為類型 **`char`** ，描述可以做為地區設定 facet 的物件，以表示類型字元之各種屬性的特性 **`char`** 。

## <a name="syntax"></a>語法

```cpp
template <>
class ctype<char>
: public ctype_base
{
public:
    typedef char _Elem;
    typedef _Elem char_type;
    bool is(
    mask _Maskval,
    _Elem _Ch) const;

    const _Elem* is(
    const _Elem* first,
    const _Elem* last,
    mask* dest) const;

    const _Elem* scan_is(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    const _Elem* scan_not(
    mask _Maskval,
    const _Elem* first,
    const _Elem* last) const;

    _Elem tolower(
    _Elem _Ch) const;

    const _Elem* tolower(
    _Elem* first,
    const _Elem* last) const;

    _Elem toupper(
    _Elem _Ch) const;

    const _Elem* toupper(
    _Elem* first,
    const _Elem* last) const;

    _Elem widen(
    char _Byte) const;

    const _Elem* widen(
    const char* first,
    const char* last,
    _Elem* dest) const;

    const _Elem* _Widen_s(
    const char* first,
    const char* last,
    _Elem* dest,
    size_t dest_size) const;

    _Elem narrow(
    _Elem _Ch,
    char _Dflt = '\0') const;

    const _Elem* narrow(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest) const;

    const _Elem* _Narrow_s(
    const _Elem* first,
    const _Elem* last,
    char _Dflt,
    char* dest,
    size_t dest_size) const;

    static locale::id& id;
    explicit ctype(
    const mask* _Table = 0,
    bool _Deletetable = false,
    size_t _Refs = 0);

protected:
    virtual ~ctype();
//other protected members
};
```

## <a name="remarks"></a>備註

明確特製化與類別樣板的差異有好幾種：

- 類別的物件會 `ctype<char>` 儲存 ctype 遮罩資料表第一個元素的指標，這是類型的 UCHAR_MAX + 1 個元素的陣列 `ctype_base::mask` 。 它也會儲存布林物件，指出當 ctype 物件終結時，是否應刪除（使用 `operator delete[]` ）陣列 \< **Elem**> 。

- 其唯一的公用函式可讓您指定 `tab` 、ctype 遮罩資料表和 `del` 布林物件，如果在物件終結時應刪除陣列，則為 true，以及 `ctype<char>` 參考計數參數 refs。

- Protected 成員函式會傳回 `table` 儲存的 ctype 遮罩資料表。

- 靜態成員物件會 `table_size` 指定 ctype 遮罩資料表中元素的最小數目。

- 受保護的靜態成員函式 `classic_table` （傳回適用于 "C" 地區設定的 ctype 遮罩資料表。

- 系統並沒有提供 [do_is](../standard-library/ctype-class.md#do_is)、[do_scan_is](../standard-library/ctype-class.md#do_scan_is) 或 [do_scan_not](../standard-library/ctype-class.md#do_scan_not) 這幾個受保護的虛擬成員函式。 對應的公用成員函式會自行執行對等作業。

成員函式 [do_narrow](../standard-library/ctype-class.md#do_narrow) 和 [do_widen](../standard-library/ctype-class.md#do_widen) 會複製不變的元素。

## <a name="requirements"></a>需求

**標頭：**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[facet 類別](locale-class.md#facet_class)\
[ctype_base 類別](../standard-library/ctype-base-class.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
