---
title: codecvt_base 類別
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt_base
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
ms.openlocfilehash: 6f957c39f9c78fd182b7ba2a14bdab7f27db56ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405296"
---
# <a name="codecvtbase-class"></a>codecvt_base 類別

Codecvt 類別用來定義列舉類型的基底類別稱為`result`用作 facet 成員函式的傳回類型，表示轉換的結果。

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

此類別描述樣板類別 [codecvt](../standard-library/codecvt-class.md) 之所有特製化通用的列舉。 列舉結果描述可能從 [do_in](../standard-library/codecvt-class.md#do_in) 或 [do_out](../standard-library/codecvt-class.md#do_out) 傳回的值：

- `ok` 如果內部和外部字元編碼之間的轉換會成功。

- `partial` 如果目的地無法夠大，才能成功轉換。

- `error` 如果來源序列的格式不，正確。

- `noconv` (如果函式不會執行任何轉換)。

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
