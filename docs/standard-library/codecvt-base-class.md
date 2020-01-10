---
title: codecvt_base 類別
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6fca9b2130407b165a7a7bfb1fb2a9ec81774e20
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689881"
---
# <a name="codecvt_base-class"></a>codecvt_base 類別

Codecvt 類別的基類，用來定義稱為 `result` 的列舉類型，做為 facet 成員函式的傳回型別，以指示轉換的結果。

## <a name="syntax"></a>語法

```cpp
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```

## <a name="remarks"></a>備註

類別描述類別樣板[codecvt](../standard-library/codecvt-class.md)的所有特製化通用的列舉。 列舉結果描述可能從 [do_in](../standard-library/codecvt-class.md#do_in) 或 [do_out](../standard-library/codecvt-class.md#do_out) 傳回的值：

- 如果內部和外部字元編碼之間的轉換成功，`ok`。

- 如果目的地不夠大，無法成功轉換，`partial`。

- 如果來源序列的格式不正確，`error`。

- `noconv` (如果函式不會執行任何轉換)。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
