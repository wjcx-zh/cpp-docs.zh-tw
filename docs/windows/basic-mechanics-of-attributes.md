---
title: 屬性的基本機制 |Microsoft Docs
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
ms.openlocfilehash: 3bb7ff68f9c17f7b90261c2c96630911454842a5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462488"
---
# <a name="basic-mechanics-of-attributes"></a>屬性的基本機制
有三種方式，將屬性插入您的專案。 首先，您可以將它們插入以手動方式插入原始程式碼中。 第二，您可以將它們插入在專案中使用物件的屬性方格。 最後，您可以將它們插入使用各種不同的精靈。 如需有關使用**屬性** 視窗和各種精靈，請參閱[Creating and Managing Visual c + + Projects](../ide/creating-and-managing-visual-cpp-projects.md)。  
  
 為之前，先建置專案時，編譯器會剖析每個 c + + 原始程式檔，產生的物件檔案。 不過，當編譯器發現屬性，它會剖析並語法驗證。 然後編譯器動態地呼叫插入程式碼，或在編譯時期進行其他修改的屬性提供者。 提供者的實作是根據屬性的類型而有所不同。 比方說，ATL 相關屬性的實作方式 Atlprov.dll。  
  
 下圖示範編譯器和屬性提供者之間的關聯性。  
  
 ![元件屬性通訊](../windows/media/vccompattrcomm.gif "vcCompAttrComm")  
  
> [!NOTE]
>  屬性使用方式不會更改原始程式檔的內容。 產生的屬性程式碼會顯示的唯一時間是在偵錯工作階段期間。 此外，在專案中每個原始程式檔，您可以產生文字檔案，以顯示屬性的替代結果。 如需有關此程序的詳細資訊，請參閱 < [/Fx （合併插入程式碼）](../build/reference/fx-merge-injected-code.md)並[偵錯插入程式碼](/visualstudio/debugger/how-to-debug-injected-code)。  
  
 大部分的 c + + 建構，例如屬性會有一組特性，定義其適當的使用方式。 這指做為屬性的內容，並在屬性內容表的每一個屬性參考主題中已解決。 例如， [coclass](../windows/coclass.md)屬性可以只套用至現有的類別或結構，而不是[cpp_quote](../windows/cpp-quote.md)屬性，可以插入 c + + 原始程式檔內的任何位置。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../windows/attributed-programming-concepts.md)