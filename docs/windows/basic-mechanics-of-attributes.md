---
title: 屬性的基本機制 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], inserting in code
- attributes [C++], about attributes
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d6db2994a2606f6c4d0cb4cd581ec46d87ca3d2c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864930"
---
# <a name="basic-mechanics-of-attributes"></a>屬性的基本機制
有三種方式，將屬性插入您的專案。 首先，您可以將其插入手動插入原始程式碼。 第二，您可以將其插入在專案中使用屬性方格的物件。 最後，您可以將其插入使用不同的精靈。 如需有關如何使用 [屬性] 視窗和各種精靈的詳細資訊，請參閱[建立和管理 Visual c + + 專案](../ide/creating-and-managing-visual-cpp-projects.md)。  
  
 為之前，建立專案時，編譯器會剖析每個 c + + 原始程式檔，產生的物件檔案。 不過，當編譯器遇到屬性時，它會剖析並語法驗證。 然後編譯器以動態方式呼叫插入程式碼，或在編譯時期進行其他修改的屬性提供者。 屬性的型別而異的提供者實作。 例如，由 Atlprov.dll 實作 ATL 相關的屬性。  
  
 下圖示範編譯器和屬性提供者之間的關聯性。  
  
 ![元件屬性通訊](../windows/media/vccompattrcomm.gif "vcCompAttrComm")  
  
> [!NOTE]
>  屬性使用方式不會改變原始程式檔的內容。 產生的屬性的程式碼會顯示唯一的時間是在偵錯工作階段期間。 此外，在專案中每個來源檔案，您可以產生文字檔案，以顯示屬性的替代結果。 如需有關這個程序的詳細資訊，請參閱[/Fx （合併插入程式碼）](../build/reference/fx-merge-injected-code.md)和[偵錯插入程式碼](/visualstudio/debugger/how-to-debug-injected-code)。  
  
 大部分的 c + + 建構，例如屬性有一組特性，定義其適當用法。 這指屬性的內容，並解決屬性內容資料表中的每個屬性參考主題。 例如， [coclass](../windows/coclass.md)屬性只會套用至現有類別或結構，與[cpp_quote](../windows/cpp-quote.md)屬性，可以插入 c + + 原始程式檔內的任何位置。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../windows/attributed-programming-concepts.md)