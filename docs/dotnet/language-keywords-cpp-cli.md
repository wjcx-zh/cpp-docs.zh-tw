---
title: 語言關鍵字 (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0b9deb25e203ea805b1430b2ec8e56f17a50123b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445434"
---
# <a name="language-keywords-ccli"></a>語言關鍵字 (C++/CLI)

從 Managed Extensions for c + + 變更為 Visual c + + 的數個語言關鍵字。

在新的 Visual c + + 語法中，雙底線會移除做為前置詞，從所有的關鍵字 (有一個例外狀況：`__identifier`保留)。 比方說，如果屬性現在宣告為`property`，而非`__property`。

沒有受管理的擴充功能中使用雙底線的前置詞的兩個主要原因：

- 它是符合標準的方法為 ISO c + + 標準提供本機的延伸模組。 Managed Extensions 設計的主要目標是要提供與標準的語言，例如新的關鍵字和語彙基元不相容。 這個原因，是設計選擇的受管理的參考型別之物件的宣告的指標語法的大型組件中。

- 使用雙底線，除了其符合標準方面，也是合理的非侵入式語言使用者現有的程式碼基底保證。 這是管理擴充功能設計的第二個主要目標。

儘管移除雙底線，Microsoft 會繼續努力要符合標準。 不過，支援在 CLR 的動態物件模型代表新且功能強大的程式設計範例。 這個新架構的支援需要它自己的高層級的關鍵字和權杖。 我們有想要提供此新架構的整合和支援標準的語言時第一級的運算式。 新的語法設計提供這兩種不同的物件模型的第一級程式設計體驗。

同樣地，我們所關注充分發揮這些新的語言關鍵字的非侵入性的本質。 這已使用的內容和含空格關鍵字來完成。 我們看看實際的新語言語法之前，讓我們試著了解這些兩個特殊關鍵字的特性。

內容關鍵字具有特殊意義的特定程式內容中。 在一般程式中，例如`sealed`會被視為一般的識別項。 不過，當出現於受管理的參考類別類型中宣告的一部分，它被視為該類別宣告的內容中的關鍵字。 這樣可以降低潛在的侵入性影響的項目簡介新的關鍵字，在語言中，我們覺得一定要與現有的程式碼基底的使用者。 在此同時，它可讓使用者的新功能的其他語言功能-項目不是使用 Managed Extensions 的頂級體驗。 如需如何的範例`sealed`可查看[Managed 類別類型的宣告](../dotnet/declaration-of-a-managed-class-type.md)。

含空格的關鍵字，例如`value class`，是內容關鍵字的特殊案例。 它的內容相關的修飾詞，以空格分隔組現有的關鍵字。 配對被視為單一單位，而不是兩個不同的關鍵字。

## <a name="see-also"></a>另請參閱

[C++/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)<br/>
[執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)