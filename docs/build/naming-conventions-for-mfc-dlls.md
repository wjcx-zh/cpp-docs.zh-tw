---
title: "MFC Dll 命名慣例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC libraries [C++], naming conventions
- naming conventions [C++], MFC DLLs
- MFC DLLs [C++], naming conventions
- libraries [C++], MFC DLL names
- shared DLL versions [C++]
- DLLs [C++], naming conventions
- DLLs [C++], library names
ms.assetid: 0db9c3f3-87d3-40e8-8964-250f9d2a2209
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7b78d01405ca74acfa74f898b88d1c9b79625e99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="naming-conventions-for-mfc-dlls"></a>MFC DLL 命名慣例
Dll 和包含在 MFC 程式庫遵循結構化的命名慣例。 這可讓您容易知道哪一個 DLL 或程式庫您應該使用哪一個用途。  
  
 建置應用程式或使用這些 Dll 的 MFC 擴充 Dll 所需的匯入程式庫與 DLL 相同的基底名稱，但有.lib 檔案的副檔名。  
  
### <a name="shared-dll-naming-convention"></a>共用的 DLL 命名慣例  
  
|DLL|描述|  
|---------|-----------------|  
|MFCx0.DLL|MFC DLL，ANSI 發行版本|  
|MFCx0U.DLL|MFC DLL，Unicode 發行版本|  
|MFCx0D.DLL|MFC DLL，ANSI 偵錯版本|  
|MFCx0UD.DLL|MFC DLL，Unicode 偵錯版本|  
  
 如果您以動態方式連結至 MFC 的共用 DLL 版本是否從應用程式，或從 MFC 擴充 DLL，您必須包含 MFCx0.DLL 與您的產品。 如果您需要支援 Unicode 應用程式中，請改為包含 MFCx0U.DLL。  
  
 如果您的 DLL 以靜態方式連結至 MFC，您必須將它與其中一個 MFC 靜態程式庫連結。 這些版本會命名為根據的慣例 [N &#124;U] AFXCW [D]。LIB。 如需詳細資訊，請參閱資料表 「 靜態連結程式庫命名慣例 」[程式庫命名慣例](../mfc/library-naming-conventions.md)(MFC)。  
  
 如需可以與您的應用程式發佈的 Visual c + + Dll 的清單，請參閱 Redist.txt Visual Studio 安裝。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [程式庫命名慣例](../mfc/library-naming-conventions.md)  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)