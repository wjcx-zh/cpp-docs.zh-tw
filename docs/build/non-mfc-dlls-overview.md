---
title: 非 MFC Dll： 概觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c61ad8e6d1107dfdacc91c32d48ca1e3624a0211
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="non-mfc-dlls-overview"></a>非 MFC DLL：概觀
非 MFC 的 DLL 會在內部，不會使用 MFC 的 DLL，而且在 DLL 中匯出的函式可以由呼叫 MFC 或非 MFC 可執行檔。 函式通常被匯出從非 MFC DLL 使用標準 C 介面。  
  
 如需非 MFC Dll 的詳細資訊，請參閱[動態連結程式庫](http://msdn.microsoft.com/library/windows/desktop/ms682589)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
## <a name="what-do-you-want-to-do"></a>請您指定選項。  
  
-   [逐步解說： 建立和使用動態連結程式庫](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [初始化 DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [以靜態方式連結至 MFC 的標準 MFC Dll](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 延伸模組 DLL：概觀](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>另請參閱  
 [DLL 的種類](../build/kinds-of-dlls.md)