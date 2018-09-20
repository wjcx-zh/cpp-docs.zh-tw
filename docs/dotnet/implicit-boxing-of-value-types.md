---
title: 實值型別的隱含 Boxing |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
- __box keyword
- boxing
- boxing, __box keyword
- value types, boxed
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e9c232dba6d766d0855bb4bb29e33d85b5fd5a2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387584"
---
# <a name="implicit-boxing-of-value-types"></a>實值類型的隱含 Boxing

實值型別的 boxing 已從 Managed Extensions for c + + Visual c + +。

在語言設計中，我們理性功能的實際經驗，並在實務上，這是錯誤。 比方說，在原始多重繼承語言設計中，Stroustrup 決定在衍生的類別建構函式，無法初始化虛擬基底類別的子物件，並因此語言所需的任何類別做為虛擬基底類別必須定義預設建構函式。 它是該預設建構函式會叫用的任何後續的虛擬衍生。

虛擬基底類別階層架構的問題是共用的虛擬子物件的初始化負責移位使用每個後續的衍生。 比方說，如果我定義的基底類別的初始化需要的緩衝區中，使用者指定的緩衝區大小配置可能會傳遞做為引數的建構函式。 如果我再提供兩個後續的虛擬衍生，稱之為`inputb`和`outputb`，每個都提供特定值的基底類別建構函式。 現在，當我衍生`in_out`類別兩者`inputb`和`outputb`，這些值，以共用虛擬基底類別的子物件都不合理允許評估。

因此，在原始的語言設計中，Stroustrup 不允許明確初始化的成員初始設定清單中的衍生的類別建構函式的虛擬基底類別。 雖然解決此問題，在實務上無法以直接的虛擬基底類別初始化證實了無法實行。 National Institute 的健全狀況，Keith Gorlen 人員必須實作呼叫 nihcl SmallTalk 集合程式庫的免費軟體版本，已在說服 Stroustrup，他必須擬定更有彈性的語言設計原則語音。

物件導向階層式設計的原則會保留在衍生的類別應該考量本身只能搭配其直接基底類別的非私用實作。 為了支援虛擬繼承彈性初始化設計，Stroustrup 必須違反這個原則。 階層中的最具衍生性的類別負責不論深度所有的虛擬子物件初始化，到它，就會發生的階層。 例如，`inputb`和`outputb`都負責明確初始化其即時的虛擬基底類別。 時`in_out`衍生自兩者`inputb`並`outputb`，`in_out`初始化一次移除虛擬基底類別，並初始化進行明確內會變成負責`inputb`和`outputb`是隱藏。

這會提供所需語言的開發人員，代價是複雜的語意的彈性。 此項負擔的複雜功能移除了如果我們限制虛擬基底類別，而無狀態，並且只允許指定的介面。 這是建議的設計慣例，c + +。 Clr 程式設計中，它就會引發以介面類型的原則。

以下是簡單的程式碼範例-，並在此案例中，明確的 boxing 處理是不必要：

```
// Managed Extensions for C++ requires explicit __box operation
int my1DIntArray __gc[] = { 1, 2, 3, 4, 5 };
Object* myObjArray __gc[] = {
   __box(26), __box(27), __box(28), __box(29), __box(30)
};

Console::WriteLine( "{0}\t{1}\t{2}", __box(0),
   __box(my1DIntArray->GetLowerBound(0)),
   __box(my1DIntArray->GetUpperBound(0)) );
```

如您所見，沒有 boxing 上的一大堆。 在 Visual c + +，實值型別是隱含的 boxing:

```
// new syntax makes boxing implicit
array<int>^ my1DIntArray = {1,2,3,4,5};
array<Object^>^ myObjArray = {26,27,28,29,30};

Console::WriteLine( "{0}\t{1}\t{2}", 0,
   my1DIntArray->GetLowerBound( 0 ),
   my1DIntArray->GetUpperBound( 0 ) );
```

## <a name="see-also"></a>另請參閱

[實值型別及其行為 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Boxing](../windows/boxing-cpp-component-extensions.md)