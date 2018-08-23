---
title: 建置屬性化的程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tlb files
- MIDL
- MIDL, linker output
- IDL files
- tlb files, building attributed programs
- .tlb files, building attributed programs
- IDL files, building
- attributes [C++], building type libraries and .idl files
- .tlb files
- .idl files, building
- type libraries, linker options for building
ms.assetid: 04997b5f-bf2c-46ec-b868-c4adebbef5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7909884a355ccad5e1bf9d18a38dd3e4690296ee
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42587503"
---
# <a name="building-an-attributed-program"></a>建置屬性化程式

Visual c + + 屬性放入您的程式碼之後，您可能想 Visual c + + 編譯器為您產生類型程式庫和.idl 檔案。 下列連結器選項建置.tlb 和.idl 檔案的說明：

- [/IDLOUT](../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)

有些專案包含多個獨立的.idl 檔案。 這些用來產生兩個以上的.tlb 檔案，並選擇性地將其繫結至資源區塊。 此案例中目前不支援 Visual c + +。

此外，Visual c + + 連結器將會輸出單一 MIDL 檔的所有相關的 IDL 屬性資訊。 會沒有辦法從單一專案中產生兩個型別程式庫。

## <a name="see-also"></a>另請參閱

[概念](../windows/attributed-programming-concepts.md)