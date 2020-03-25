---
title: type_info 類別
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 7a016fe8fee4e5765e6172184bfa9c90eecbc687
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160667"
---
# <a name="type_info-class"></a>type_info 類別

**Type_info**類別描述編譯器在程式內產生的型別資訊。 這個類別的物件會實際儲存類型的名稱指標。 **Type_info**類別也會儲存編碼的值，適合用來比較兩個類型的相等或排序次序。 類型的編碼規則和排序法則不會指定，而且在不同的程式之間也會有所差異。

必須包含 `<typeinfo>` 標頭檔，才能使用**type_info**類別。 **Type_info**類別的介面為：

```cpp
class type_info {
public:
    type_info(const type_info& rhs) = delete; // cannot be copied
    virtual ~type_info();
    size_t hash_code() const;
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    type_info& operator=(const type_info& rhs) = delete; // cannot be copied
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    size_t hash_code() const noexcept;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

您無法直接具現化**type_info**類別的物件，因為類別只有私用複製的函式。 建立（暫時性） **type_info**物件的唯一方式是使用[typeid](../cpp/typeid-operator.md)運算子。 因為指派運算子也是私用的，所以您無法複製或指派類別**type_info**的物件。

`type_info::hash_code` 定義雜湊函式，適用于將**typeinfo**類型的值對應到索引值的分佈。

運算子 `==` 和 `!=` 可以分別用來比較是否相等，以及與其他**type_info**物件的不相等。

類型的排序順序和繼承關係之間並無連結。 使用 `type_info::before` 成員函式來判斷類型的排序次序。 不保證 `type_info::before` 會在不同的程式中產生相同的結果，甚至是相同程式的不同執行。 如此一來，`type_info::before` 類似 `(&)` 運算子的位址。

`type_info::name` 成員函式會將 `const char*` 傳回為以 null 終止的字串，代表人類可讀取的類型名稱。 所指向的記憶體會加以快取，且絕不可直接取消配置。

`type_info::raw_name` 成員函式會將 `const char*` 傳回為以 null 終止的字串，代表物件類型的裝飾名稱。 這個名稱實際上是以其裝飾形式儲存，以節省空間。 因此，此函數的速度會比 `type_info::name` 快，因為它不需要 undecorate 名稱。 `type_info::raw_name` 函數所傳回的字串在比較作業中很有用，但無法讀取。 如果您需要人類可讀的字串，請改用 `type_info::name` 函數。

只有在指定[/GR （啟用執行時間類型資訊）](../build/reference/gr-enable-run-time-type-information.md)編譯器選項時，才會針對多型類別產生類型資訊。

## <a name="see-also"></a>另請參閱

[執行階段類型資訊](../cpp/run-time-type-information.md)
