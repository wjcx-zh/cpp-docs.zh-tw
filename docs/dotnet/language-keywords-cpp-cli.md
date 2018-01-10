---
title: "語言關鍵字 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: keywords [C++]
ms.assetid: 021013b2-70ac-4df9-aa77-4af1c67a1a67
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e1107ad45feaae470ed2a7481f80bb17c389042d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="language-keywords-ccli"></a>語言關鍵字 (C++/CLI)
從 Managed Extensions for c + + 變更為 Visual c + + 的數個語言關鍵字。  
  
 在新的 Visual c + + 語法中，兩個底線移除了從所有關鍵字的前置詞 (有一個例外狀況：`__identifier`保留)。 比方說，如果屬性現在宣告為`property`，而非`__property`。  
  
 共有兩個受管理的擴充功能中使用雙底線前置詞的主要原因：  
  
-   它是符合 ISO c + + 標準提供本機的擴充功能的方法。 Managed Extensions 設計的主要目標是導入的標準語言，例如新的關鍵字和語彙基元不相容。 它是這個原因，在大型的部分，基於選擇的受管理的參考類型的物件宣告指標語法。  
  
-   正在非侵入性功能的語言使用者現有的程式碼基底是為了確保您也使用雙底線，除了一致性的考量。 這是管理擴充功能設計的第二個主要目標。  
  
 即便移除雙底線，Microsoft 會維持重視一致性。 但是，CLR 動態物件模型表示功能強大的程式設計範例的支援。 這個新的開發架構的支援需要它自己的高層級的關鍵字和語彙基元。 我們已提供的這個新的開發架構加以整合及支援的標準語言時，第一級的運算式進行搜尋。 新的語法設計會提供這兩個不同的物件模型的第一個類別的程式設計體驗。  
  
 同樣地，我們也注意這些新的語言關鍵字的非侵入性功能的本質。 這即已完成與內容和空格關鍵字使用。 我們會審視實際的新語言語法之前，我們來試試意義的這些兩個特殊關鍵字的特性。  
  
 內容關鍵字具有特殊意義內特定程式內容。 在一般程式，例如，內`sealed`會被視為一般識別項。 不過，受管理的參考類別類型中宣告的部分內時，它被視為該類別宣告的內容中的關鍵字。 這個影響降到最低潛在侵入性功能的項目引入新的關鍵字，在語言中，我們認為非常重要，讓使用者與現有的程式碼基底。 同時，它可讓使用者的新功能有其他語言功能的項目不是使用 Managed Extensions 的第一級的體驗。 如需如何`sealed`用看到[的受管理的類別類型宣告](../dotnet/declaration-of-a-managed-class-type.md)。  
  
 含空格的關鍵字，例如`value class`，是內容關鍵字的特殊案例。 其內容的修飾詞，以空格分隔組現有的關鍵字。 此配對被視為當做單一單位，而不是兩個不同的關鍵字。  
  
## <a name="see-also"></a>請參閱  
 [C + + /CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)   
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)