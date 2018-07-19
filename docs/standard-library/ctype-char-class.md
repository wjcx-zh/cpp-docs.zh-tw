---
title: ctype&lt;char&gt; 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- ctype<char>
- locale/std::ctype<char>
dev_langs:
- C++
helpviewer_keywords:
- ctype<char> class
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47ac9fa5431b5edfb4885dfdbf39be6c6b89cee6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960657"
---
# <a name="ctypeltchargt-class"></a>ctype&lt;char&gt; 類別

類別是範本類別明確特製化`ctype\<CharType>`鍵入**char**，描述可以做為地區設定 facet 的型別之字元各種屬性特性的物件**char**.

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

明確特製化和範本類別有下列幾項差異：

- Ctype 類別的物件 < `char`> 會儲存 ctype 遮罩資料表的第一個元素，陣列的 UCHAR_MAX + 1 個元素的類型指標`ctype_base::mask`。 它也會儲存 Boolean 物件，指出當 ctype\< **Elem**> 物件已終結時，是否應該刪除陣列 (使用 `operator delete[]`)。

- 其唯一的公用建構函式可讓您指定`tab`，ctype 遮罩資料表中，並`del`，如果陣列應該則為 true 的布林值物件刪除 ctype < `char`> 物件終結時，以及參考計數參數 refs。

- 受保護的成員函式`table`傳回預存的 ctype 遮罩資料表。

- 靜態成員物件`table_size`ctype 遮罩資料表中指定的項目數目下限。

- 受保護的靜態成員函式`classic_table`（傳回 ctype 遮罩資料表適用於"C"地區設定。

- 系統並沒有提供 [do_is](../standard-library/ctype-class.md#do_is)、[do_scan_is](../standard-library/ctype-class.md#do_scan_is) 或 [do_scan_not](../standard-library/ctype-class.md#do_scan_not) 這幾個受保護的虛擬成員函式。 對應的公用成員函式會自行執行對等作業。

成員函式 [do_narrow](../standard-library/ctype-class.md#do_narrow) 和 [do_widen](../standard-library/ctype-class.md#do_widen) 會複製不變的元素。

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[facet 類別](http://msdn.microsoft.com/Library/dd4f12f5-cb1b-457f-af56-2fb204216ec1)<br/>
[ctype_base 類別](../standard-library/ctype-base-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
