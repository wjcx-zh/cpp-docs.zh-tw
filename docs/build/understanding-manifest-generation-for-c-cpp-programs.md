---
title: "了解 C/c + + 程式的資訊清單產生過程 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 848b4b449fa2c9c8930a616b70a5b61cb28d8fbf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>了解 C/C++ 程式的資訊清單產生過程
A[資訊清單](http://msdn.microsoft.com/library/aa375365)可以是外部的 XML 檔案或資源的 XML 文件內嵌於應用程式或組件。 資訊清單的[隔離應用程式](http://msdn.microsoft.com/library/aa375190)用來管理的名稱和共用的並存組件的應用程式應繫結在執行階段版本。 並存組件資訊清單指定名稱、 版本、 資源和其他組件及其相依性。  
  
 有兩種方式可建立隔離的應用程式或-並存組件資訊清單。 首先，組件的作者，可以手動建立下列規則與命名需求的資訊清單檔案。 或者，如果程式只相依於 Visual c + + 組件，例如 CRT、 MFC、 ATL 或其他項目，然後資訊清單可以自動產生連結器。  
  
 Visual c + + 程式庫標頭則包含組件資訊，並在應用程式程式碼中的程式庫時，連結器會使用此組件資訊以最終二進位檔的資訊清單。 連結器不會內嵌於二進位檔，資訊清單檔案，並只會產生資訊清單做為外部檔案。 將資訊清單做為外部檔案可能不適用於所有案例。 例如，建議您使用私用組件有內嵌資訊清單。 在命令列組建中使用 nmake 建置程式碼，例如，資訊清單可以內嵌使用資訊清單工具;如需詳細資訊，請參閱[在命令列的資訊清單產生](../build/manifest-generation-at-the-command-line.md)。 在建置時[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，您可以內嵌資訊清單設定中的資訊清單工具屬性**專案屬性**對話方塊，請參閱 < [Visual Studio 中的資訊清單產生](../build/manifest-generation-in-visual-studio.md)。  
  
## <a name="see-also"></a>請參閱  
 [隔離的應用程式和-並存組件的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)