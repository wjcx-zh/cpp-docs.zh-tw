---
title: iostream 慣例
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 7bfc497ec7c55a611d29cd62d076c0ac2e9b6e9f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845454"
---
# <a name="iostreams-conventions"></a>iostream 慣例

iostream 標頭支援文字與編碼形式之間的轉換，以及輸入或輸出到外部檔案：

[\<fstream>](../standard-library/fstream.md)\
[\<iomanip>](../standard-library/iomanip.md)\
[\<ios>](../standard-library/ios.md)\
[\<iosfwd>](../standard-library/iosfwd.md)\
[\<iostream>](../standard-library/iostream.md)\
[\<istream>](../standard-library/istream.md)\
[\<ostream>](../standard-library/ostream.md)\
[\<sstream>](../standard-library/sstream.md)\
[\<streambuf>](../standard-library/streambuf.md)\
[\<strstream>](../standard-library/strstream.md)

Iostreams 最簡單的使用方式只需要包含標頭 [\<iostream>](../standard-library/iostream.md) 。 接著，您便可以從 [cin](../standard-library/iostream.md#cin) 或 [wcin](../standard-library/iostream.md#wcin) 擷取值來讀取標準輸入。 如需有關此做法規則的概要說明，請參閱 [basic_istream 類別](../standard-library/basic-istream-class.md)的說明。 您也可以將值插入到 [cout](../standard-library/iostream.md#cout) 或 [wcout](../standard-library/iostream.md#wcout) 來寫入標準輸出。 如需有關此做法規則的概要說明，請參閱 [basic_ostream 類別](../standard-library/basic-ostream-class.md)的說明。 擷取器和插入器都通用的格式控制項是由 [basic_ios 類別](../standard-library/basic-ios-class.md)管理。 在擷取和插入物件的掩飾下操作此格式資訊，屬於數個操作工具的領域。

您可以使用中宣告的類別，對您依名稱開啟的檔案執行相同的 iostreams 作業 [\<fstream>](../standard-library/fstream.md) 。 若要在 [Basic_string 類別](../standard-library/basic-string-class.md)的類別 iostreams 和物件之間轉換，請使用中宣告的類別 [\<sstream>](../standard-library/sstream.md) 。 若要使用 C 字串來執行相同的動作，請使用中宣告的類別 [\<strstream>](../standard-library/strstream.md) 。

其餘的標頭會提供支援服務，通常是只與 iostream 類別的最進階使用者直接相關。

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫總覽](../standard-library/cpp-standard-library-overview.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
