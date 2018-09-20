---
title: C + + /cli 移轉入門 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88b32ea226971c0fa5b6d269a8992629c3c4de77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385427"
---
# <a name="ccli-migration-primer"></a>C++/CLI 移轉入門

這是邁向您的 Visual c + + 程式從 Managed Extensions for c + + Visual c + + 的指南。

C + + /cli CLI 擴充成 ISO-C + + 標準語言的動態元件程式設計開發。 新的語言會提供優於 Managed Extensions 的重大改進功能的數字。 本章節會提供 Managed Extensions for c + + 語言功能的列舉的清單和其對應到 Visual c + + 這類對應存在，而且將點出對應不存在，這些建構的位置。

## <a name="in-this-section"></a>本節內容

[變更的大綱 (C++/CLI)](../dotnet/outline-of-changes-cpp-cli.md)<br/>
快速參考，提供分為五大類別的清單，以變更的高階大綱。

[語言關鍵字 (C++/CLI)](../dotnet/language-keywords-cpp-cli.md)<br/>
討論語言關鍵字，包括雙底線的移除以及內容和含空格關鍵字引進的變更。

[Managed 類型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
語法變更，在宣告中的一般類型系統 (CTS)-這會包括變更的類別、 陣列 （包括參數陣列）、 列舉等宣告中。

[在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
提供關於類別成員，例如純量屬性、 索引屬性、 運算子、 委派和事件的變更。

[實值型別及其行為 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
著重於實值類型和新的內部和 pin 指標系列。 它也會討論一些重大的語意變更，例如隱含 boxing、 boxed 實的值類型的不變性以及數值類別中的預設建構函式的支援的移除簡介。

[一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
詳細說明語意變更，例如轉換通知的支援字串常值的行為，並變更在語意 ISO c + + 和 C + + /cli CLI。

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)