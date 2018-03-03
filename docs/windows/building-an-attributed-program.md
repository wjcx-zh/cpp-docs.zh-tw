---
title: "建置屬性化的程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3e39bbd2b630d35942c1c5107041b2fbadf7549
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="building-an-attributed-program"></a>建置屬性化程式
Visual c + + 屬性放入您的程式碼之後，您可能想 Visual c + + 編譯器，來為您產生類型程式庫和.idl 檔案。 下列連結器選項可協助您組建.tlb 和.idl 檔案：  
  
-   [/IDLOUT](../build/reference/idlout-name-midl-output-files.md)  
  
-   [/IGNOREIDL](../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)  
  
-   [/ MIDL](../build/reference/midl-specify-midl-command-line-options.md)  
  
-   [/TLBOUT](../build/reference/tlbout-name-dot-tlb-file.md)  
  
 某些專案都包含多個獨立的.idl 檔案。 這些用來產生兩個或多個.tlb 檔案，並選擇性地將其繫結到資源區塊。 此案例中目前不支援 Visual c + + 中。  
  
 此外，Visual c + + 連結器會輸出所有單一 MIDL 檔的 IDL 相關的屬性資訊。 會從單一專案中產生兩個型別程式庫沒有方法。  
  
## <a name="see-also"></a>請參閱  
 [概念](../windows/attributed-programming-concepts.md)