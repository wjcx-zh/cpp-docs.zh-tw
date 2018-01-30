---
title: "C + + /CLI 移轉入門 |Microsoft 文件"
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
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 17474b347a6daf2d477a6ed731e13db86e068b05
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="ccli-migration-primer"></a>C++/CLI 移轉入門
這是前往 Visual c + + 程式從 Managed Extensions for c + + Visual c + + 的指引。 
  
 C + + CLI 延伸 ISO c + + 標準語言的動態元件程式設計典範。 新的語言提供顯著的改善了許多透過 Managed Extensions。 本章節會提供 Managed Extensions for c + + 語言功能的列舉的清單以及其對應至 Visual c + +，這類對應存在，而且將點出對應不存在，這些建構。  
  
## <a name="in-this-section"></a>本節內容  
 [變更的大綱 (C++/CLI)](../dotnet/outline-of-changes-cpp-cli.md)  
 提供快速參考五大類別提供的變更清單的重要概述。  
  
 [語言關鍵字 (C++/CLI)](../dotnet/language-keywords-cpp-cli.md)  
 討論語言關鍵字，包括在雙底線移除與內容和空格關鍵字引入的變更。  
  
 [Managed 類型 (C + + CL)](../dotnet/managed-types-cpp-cl.md)  
 探討語法變更，在宣告中的一般類型系統 (CTS)-這會包括變更宣告中的類別、 陣列 （包括參數陣列）、 列舉、 等等。  
  
 [在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 顯示包含類別的成員，例如純量屬性、 索引屬性、 運算子、 委派和事件的變更。  
  
 [實值型別及其行為 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 著重於實值類型和新的系列的內部和 pin 指標。 它也會討論一些重要的語意變更例如隱含 boxing、 boxed 實的值類型的不變性和支援實值類別中的預設建構函式中移除的簡介。  
  
 [一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)  
 詳細資料的語意變更支援轉型的表示法，例如字串常值的行為，以及變更在語意 ISO c + + 和 C + + /CLI。  
  
## <a name="see-also"></a>請參閱  
 [混合 （原生和 Managed） 組件](../dotnet/mixed-native-and-managed-assemblies.md)   
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)