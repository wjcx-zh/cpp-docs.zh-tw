---
title: 明確初始化
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 0b1290bc23c56c0f35ddd3bb93e37ce4f5f0d2ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361952"
---
# <a name="explicit-instantiation"></a>明確初始化

您可以使用明確具現化，建立樣板化類別或函式的具現化，而在程式碼中實際使用它。 由於當您建立使用樣板散發的程式庫 (.lib) 檔案時，這樣做很有用的，未具現化的樣板定義不會進入目的檔 (.obj)。

此代碼顯示式實體化`MyStack`**int**變數和六個專案:

```cpp
template class MyStack<int, 6>;
```

這個陳述式建立 `MyStack` 的具現化，沒有保留物件的任何儲存區。 程式碼為所有成員產生。

下一行只明確具現化建構函式成員函式：

```cpp
template MyStack<int, 6>::MyStack( void );
```

可以使用特定類型參數顯式實例化函數範本以重新聲明它們,如[函數範本實例化](../cpp/function-template-instantiation.md)中的示例所示。

您可以使用**extern**關鍵字來防止成員的自動實例化。 例如：

```cpp
extern template class MyStack<int, 6>;
```

同樣地，您可以將特定成員標記為外部和未具現化：

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

可以使用**extern**關鍵字來防止編譯器在多個物件模組中生成相同的實例化代碼。 如果函式被呼叫，您必須在至少一個連結模組中使用指定的明確樣板參數，來具現化樣板函式，否則當程式建立時會發生連結器錯誤。

> [!NOTE]
> 專業化化中的**extern**關鍵字僅適用於在類正文之外定義的成員函數。 類別宣告內定義的函式被視為內嵌函式，永遠會具現化。

## <a name="see-also"></a>另請參閱

[函數範本](../cpp/function-templates.md)
