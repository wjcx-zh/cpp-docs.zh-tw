---
title: "記憶體管理與 CStringT |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringT
- ATL::CStringT
- ATL.CStringT
dev_langs: C++
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbf623344ec52abce28a08670e7f3cd09140563b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-with-cstringt"></a>CStringT 使用記憶體管理
類別[CStringT](../atl-mfc-shared/reference/cstringt-class.md)是範本類別，用來操作可變長度的字元字串。 要保留這些字串的記憶體配置和釋放與每個執行個體相關聯的字串管理員物件透過`CStringT`。 MFC 和 ATL 提供的預設具現化`CStringT`，稱為`CString`， `CStringA`，和`CStringW`的操作不同的字元類型的字串。 這些字元類型屬於類型**TCHAR**， `char`，和`wchar_t`分別。 這些預設字串型別會使用字串管理員，會從程序中的堆積 （ATL) 或 （MFC) 中的 CRT 堆積配置記憶體。 對於一般應用程式，此記憶體配置方案已足夠。 不過，大量的程式碼使用的字串 （或多執行緒程式碼），預設記憶體管理員可能無法充分執行。 本主題說明如何覆寫的預設記憶體管理行為`CStringT`，特別建立的配置器適合手邊的工作。  
  
-   [自訂字串管理員實作 (基本方法)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)  
  
-   [避免堆積競爭](../atl-mfc-shared/avoidance-of-heap-contention.md)  
  
-   [自訂字串管理員實作 (進階方法)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)  
  
-   [CFixedStringT： 範例的自訂字串管理員](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)  
  
## <a name="see-also"></a>請參閱  
 [CustomString 範例](../visual-cpp-samples.md)

