---
title: "建議使用的文件註解 （Visual c + +） 標籤 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65d2161edc4b2aa03cd547467ca0f38158850051
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>建議使用的文件註解標記 (Visual C++)
Visual c + + 編譯器將會處理在程式碼中的文件註解，並建立.xdc 檔案以供每個編譯單位中，並 xdcmake.exe 會處理到.xml 檔.xdc 檔。 處理要建立文件的.xml 檔案是必須位於您網站實作詳細資料。  
  
 標記會在建構，例如型別上處理和類型成員。  
  
 標記必須緊接著類型或成員。  
  
> [!NOTE]
>  文件註解無法套用至命名空間，或在超出定義的屬性和事件;文件註解必須在類別內宣告。  
  
 編譯器會處理任何為有效 XML 的標記。 下列標記會提供使用者文件中的常用的功能：  
  
||||  
|-|-|-|  
|[\<c>](../ide/c-visual-cpp.md)|[\<code>](../ide/code-visual-cpp.md)|[\<example>](../ide/example-visual-cpp.md)|  
|[\<例外狀況 >](../ide/exception-visual-cpp.md)1|[\<包含 >](../ide/include-visual-cpp.md)1|[\<list>](../ide/list-visual-cpp.md)|  
|[\<para>](../ide/para-visual-cpp.md)|[\<param >](../ide/param-visual-cpp.md)1|[\<paramref >](../ide/paramref-visual-cpp.md)1|  
|[\<權限 >](../ide/permission-visual-cpp.md)1|[\<remarks>](../ide/remarks-visual-cpp.md)|[\<returns>](../ide/returns-visual-cpp.md)|  
|[\<請參閱 >](../ide/see-visual-cpp.md)1|[\<另請參閱 >](../ide/seealso-visual-cpp.md)1|[\<summary>](../ide/summary-visual-cpp.md)|  
|[\<value>](../ide/value-visual-cpp.md)|||  
  
 1. 編譯器會驗證語法。  
  
 在目前版本中，Visual c + + 編譯器不支援`<paramref>`，其他 Visual Studio 編譯器所支援的標記。 Visual c + + 可能支援`<paramref>`未來的版本。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)