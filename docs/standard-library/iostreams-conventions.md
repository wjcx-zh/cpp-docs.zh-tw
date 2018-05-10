---
title: iostream 慣例 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37ba52981f317ff9929a820c42d35cde0506256f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="iostreams-conventions"></a>iostream 慣例

iostream 標頭支援文字與編碼形式之間的轉換，以及輸入或輸出到外部檔案：

|||
|-|-|
|[\<fstream>](../standard-library/fstream.md)|[\<iomanip>](../standard-library/iomanip.md)|
|[\<ios>](../standard-library/ios.md)|[\<iosfwd>](../standard-library/iosfwd.md)|
|[\<iostream>](../standard-library/iostream.md)|[\<istream>](../standard-library/istream.md)|
|[\<ostream>](../standard-library/ostream.md)|[\<sstream>](../standard-library/sstream.md)|
|[\<streambuf>](../standard-library/streambuf.md)|[\<strstream>](../standard-library/strstream.md)|

最簡單的 iostream 使用方式只需您包含 [\<iostream>](../standard-library/iostream.md) 標頭。 接著，您便可以從 [cin](../standard-library/iostream.md#cin) 或 [wcin](../standard-library/iostream.md#wcin) 擷取值來讀取標準輸入。 如需有關此做法規則的概要說明，請參閱 [basic_istream 類別](../standard-library/basic-istream-class.md)的說明。 您也可以將值插入到 [cout](../standard-library/iostream.md#cout) 或 [wcout](../standard-library/iostream.md#wcout) 來寫入標準輸出。 如需有關此做法規則的概要說明，請參閱 [basic_ostream 類別](../standard-library/basic-ostream-class.md)的說明。 擷取器和插入器都通用的格式控制項是由 [basic_ios 類別](../standard-library/basic-ios-class.md)管理。 在擷取和插入物件的掩飾下操作此格式資訊，屬於數個操作工具的領域。

您可以使用在 [\<fstream>](../standard-library/fstream.md) 中宣告的類別，在依名稱開啟的檔案上執行相同的 iostream 作業。 若要在 iostream 與 [basic_string 類別](../standard-library/basic-string-class.md)的物件之間進行轉換，請使用在 [\<sstream>](../standard-library/sstream.md) 中宣告的類別。 若要使用 C 字串來進行相同的作業，請使用在 [\<strstream>](../standard-library/strstream.md) 中宣告的類別。

其餘的標頭會提供支援服務，通常是只與 iostream 類別的最進階使用者直接相關。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
