---
title: 建置屬性化的程式 |Microsoft 文件
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
ms.openlocfilehash: 9d87f95b456e3f99598f48e6ffa8ad29806aa168
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="building-an-attributed-program"></a>建置屬性化程式
Visual c + + 屬性放入您的程式碼之後，您可能想 Visual c + + 編譯器，來為您產生類型程式庫和.idl 檔案。 下列連結器選項可協助您組建.tlb 和.idl 檔案：  
  
-   [/IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 某些專案都包含多個獨立的.idl 檔案。 這些用來產生兩個或多個.tlb 檔案，並選擇性地將其繫結到資源區塊。 此案例中目前不支援 Visual c + + 中。  
  
 此外，Visual c + + 連結器會輸出所有單一 MIDL 檔的 IDL 相關的屬性資訊。 會從單一專案中產生兩個型別程式庫沒有方法。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../windows/attributed-programming-concepts.md)