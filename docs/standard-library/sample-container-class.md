---
title: 範例容器類別
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: 2024574633069cc70f0885fdce63f3afc09227c0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451101"
---
# <a name="sample-container-class"></a>範例容器類別

> [!NOTE]
> 本主題位於 Microsoft C++檔中, 做為C++標準程式庫中所使用之容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

描述控制不同長度專案序列 (通常是類型`Ty`) 的物件。 序列會根據實際容器，以不同方式儲存。

容器建構函式或成員函式可能會發現呼叫建構函式 **Ty**(**const Ty&** ) 或函式 **Ty::operator=** (**const Ty&** ) 的情況。 如果這類呼叫擲回例外狀況，容器物件就必須維持其完整性，並重新擲回它攔截到的任何例外狀況。 在它擲回這其中一個例外狀況之後，您就能安全地交換、指派、清除或終結容器物件。 不過，一般來說，您無法以其他方式預測容器物件所控制的序列狀態。

一些其他注意事項：

- 如果運算式`~Ty`擲回例外狀況, 則會產生未定義的容器物件狀態。

- 如果容器儲存配置器物件*al*, 而*al*擲回例外狀況, 而不是呼叫`al.allocate`的結果, 則會產生未定義的容器物件狀態。

- 如果容器會儲存函式物件 *comp* 來決定如何排序受控制的序列，而且 *comp* 擲回任何種類的例外狀況，則會產生未定義的容器物件狀態。

C++ 標準程式庫所定義的容器類別會符合數個額外的需求，如下列段落中所述。

容器樣板類別 [list](../standard-library/list-class.md) 提供決定性且實用的行為，即使出現上述例外狀況也很有用。 例如，如果在插入一或多個項目時擲回例外狀況，容器就會保持不變，並重新擲回例外狀況。

針對 C++標準程式庫所定義的所有容器類別, 如果在呼叫下列成員函式、 `insert` `push_back`、或`push_front`時擲回例外狀況, 則容器會原封不動地保留, 而例外狀況為狀況.

針對 C++標準程式庫所定義的所有容器類別, 呼叫下列成員函式期間不會擲回例外`pop_back`狀況`pop_front`:、。

只有在複製作業 (指派或複製建構) 擲回例外狀況時，成員函式 [erase](../standard-library/container-class-erase.md) 才會擲回例外狀況。

此外，在複製成員函式所傳回的迭代器時，不會擲回任何例外狀況。

成員函式 [swap](../standard-library/container-class-swap.md) 會針對 C++ 標準程式庫所定義的 all 容器類別做出額外承諾：

- 只有在容器儲存配置器物件 al，且 `al` 在複製時擲回例外狀況，成員函式才會擲回例外狀況。

- 用以指定要交換之受控制序列項目的參考、指標和迭代器會保持有效狀態。

C++ 標準程式庫所定義的容器類別物件會透過 `Alloc` 類型的預存物件，配置並釋放它所控制之序列的儲存體，此物件通常是樣板參數。 這種配置器物件必須具有與類別`allocator<Ty>`的物件相同的外部介面。 特別的是`Alloc` , 必須與相同的類型`Alloc::rebind<value_type>::other`

針對 C++標準程式庫所定義的所有容器類別, `Alloc get_allocator const;`此成員函式會傳回預存配置器物件的複本。 請注意，如果已指派容器物件，就不會複製預存的配置器物件。 所有的函式會將儲存`allocator`在中`Alloc`的值初始化, 如果此函式未包含配置器參數, 則為。

根據 C++ 標準，C++ 標準程式庫所定義的容器類別可能會假設：

- `Alloc` 類別的所有物件都會比較是否相等。

- 類型`Alloc::const_pointer` 與`const Ty *`相同。

- 類型`Alloc::const_reference` 與`const Ty&`相同。

- 類型`Alloc::pointer` 與`Ty *`相同。

- 類型`Alloc::reference` 與`Ty&`相同。

不過，在此實作中，容器不會進行這類簡化的假設。 因此，它們能夠搭配範圍更廣泛的配置器物件正常運作：

- `Alloc` 類別的所有物件都不需要比較是否相等 (您可以維護多個儲存體集區)。

- 類型`Alloc::const_pointer`不需要與`const Ty *`相同。 (const 指標可以是類別)。

- 類型`Alloc::pointer`不需要與`Ty *`相同。 (指標可以是類別)。

## <a name="requirements"></a>需求

**標頭**：\<sample container>

## <a name="see-also"></a>另請參閱

[\<範例容器>](../standard-library/sample-container.md)
