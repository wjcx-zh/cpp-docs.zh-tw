---
title: 範例容器類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 004da50bf8d688f1d7b0432e5196094b878870cf
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955003"
---
# <a name="sample-container-class"></a>範例容器類別

> [!NOTE]
> 本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

描述控制不同長度序列的項目，通常是型別物件`Ty`。 序列會根據實際容器，以不同方式儲存。

容器建構函式或成員函式可能會發現呼叫建構函式 **Ty**(**const Ty&**) 或函式 **Ty::operator=**(**const Ty&**) 的情況。 如果這類呼叫擲回例外狀況，容器物件就必須維持其完整性，並重新擲回它攔截到的任何例外狀況。 在它擲回這其中一個例外狀況之後，您就能安全地交換、指派、清除或終結容器物件。 不過，一般來說，您無法以其他方式預測容器物件所控制的序列狀態。

一些其他注意事項：

- 如果運算式`~Ty`擲回例外狀況，產生的容器物件狀態是未定義。

- 如果容器儲存配置器物件*al*，並*al*就會擲回以外的例外狀況，由於呼叫 * al ***.allocate**，產生的容器狀態物件是未定義。

- 如果容器會儲存函式物件 *comp* 來決定如何排序受控制的序列，而且 *comp* 擲回任何種類的例外狀況，則會產生未定義的容器物件狀態。

C++ 標準程式庫所定義的容器類別會符合數個額外的需求，如下列段落中所述。

容器樣板類別 [list](../standard-library/list-class.md) 提供決定性且實用的行為，即使出現上述例外狀況也很有用。 例如，如果在插入一或多個項目時擲回例外狀況，容器就會保持不變，並重新擲回例外狀況。

針對*所有*容器所定義的類別 c + + 標準程式庫，如果下列成員函式呼叫期間擲回例外狀況`insert`， `push_back`，或`push_front`，容器會保持不變，重新擲回例外狀況。

針對*所有*c + + 標準程式庫所定義的容器類別，不會擲回例外狀況呼叫下列成員函式： `pop_back`， `pop_front`。

只有在複製作業 (指派或複製建構) 擲回例外狀況時，成員函式 [erase](../standard-library/container-class-erase.md) 才會擲回例外狀況。

此外，在複製成員函式所傳回的迭代器時，不會擲回任何例外狀況。

成員函式 [swap](../standard-library/container-class-swap.md) 會針對 C++ 標準程式庫所定義的 all 容器類別做出額外承諾：

- 只有在容器儲存配置器物件 al，且 `al` 在複製時擲回例外狀況，成員函式才會擲回例外狀況。

- 用以指定要交換之受控制序列項目的參考、指標和迭代器會保持有效狀態。

C++ 標準程式庫所定義的容器類別物件會透過 `Alloc` 類型的預存物件，配置並釋放它所控制之序列的儲存體，此物件通常是樣板參數。 這類配置器物件必須具有相同的外部介面的類別物件`allocator<Ty>`。 特別是，`Alloc`必須是相同的型別 `Alloc::rebind<value_type>::other`

針對*所有*c + + 標準程式庫，此成員函式所定義的容器類別`Alloc get_allocator const;`傳回的預存配置器物件複本。 請注意，如果已指派容器物件，就不會複製預存的配置器物件。 所有建構函式初始化中儲存的值`allocator`至`Alloc`如果建構函式中不包含任何的配置器參數。

根據 C++ 標準，C++ 標準程式庫所定義的容器類別可能會假設：

- `Alloc` 類別的所有物件都會比較是否相等。

- 型別`Alloc::const_pointer`等同於`const Ty *`。

- 型別`Alloc::const_reference`等同於`const Ty&`。

- 型別`Alloc::pointer`等同於`Ty *`。

- 型別`Alloc::reference`等同於`Ty&`。

不過，在此實作中，容器不會進行這類簡化的假設。 因此，它們能夠搭配範圍更廣泛的配置器物件正常運作：

- `Alloc` 類別的所有物件都不需要比較是否相等 (您可以維護多個儲存體集區)。

- 型別`Alloc::const_pointer`不需要相同`const Ty *`。 (const 指標可以是類別)。

- 型別`Alloc::pointer`不需要相同`Ty *`。 (指標可以是類別)。

## <a name="requirements"></a>需求

**標頭**：\<sample container>

## <a name="see-also"></a>另請參閱

[\<範例容器>](../standard-library/sample-container.md)<br/>
