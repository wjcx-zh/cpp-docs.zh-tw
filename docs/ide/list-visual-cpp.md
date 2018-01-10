---
title: "&lt;清單&gt;（Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- list
- <list>
dev_langs: C++
helpviewer_keywords:
- list C++ XML tag
- <list> C++ XML tag
ms.assetid: c792a10b-0451-422c-9aa0-604116e69d64
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e04fb5f7ff2ba22b53c0fe163455bfdb666f9b9f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ltlistgt-visual-c"></a>&lt;清單&gt;（Visual c + +）
\<listheader> 區塊用來定義資料表或定義清單的標題資料列。 定義資料表時，您只需要提供標題中詞彙的項目。  
  
## <a name="syntax"></a>語法  
  
```  
<list type="bullet" | "number" | "table">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>參數  
 `term`  
 要定義的詞彙，可定義於 `description` 中。  
  
 `description`  
 項目符號或編號清單中的項目或者 `term` 的定義。  
  
## <a name="remarks"></a>備註  
 清單中的每個項目都是使用 \<item> 區塊所指定。 建立定義清單時，您需要同時指定 `term` 和 `description`。 不過，針對資料表、項目符號清單或編號清單，您只需要提供 `description` 的項目。  
  
 清單或資料表可以有所需的多個 \<item> 區塊。  
  
 編譯搭配 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 可處理檔案的文件註解。  
  
## <a name="example"></a>範例  
  
```  
// xml_list_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_list_tag.dll  
/// <remarks>Here is an example of a bulleted list:  
/// <list type="bullet">  
/// <item>  
/// <description>Item 1.</description>  
/// </item>  
/// <item>  
/// <description>Item 2.</description>  
/// </item>  
/// </list>  
/// </remarks>  
class MyClass {};  
```  
  
## <a name="see-also"></a>請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)