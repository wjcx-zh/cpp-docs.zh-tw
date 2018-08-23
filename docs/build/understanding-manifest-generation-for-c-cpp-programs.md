---
title: 了解 C/c + + 程式的資訊清單產生過程 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40dbc61009cdfaa5621335cfb78dd10eae2138ca
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572815"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>了解 C/C++ 程式的資訊清單產生過程
A[資訊清單](http://msdn.microsoft.com/library/aa375365)內嵌在應用程式或組件的 XML 文件可以是外部的 XML 檔案或資源。 資訊清單[隔離的應用程式](http://msdn.microsoft.com/library/aa375190)用來管理的名稱和共用的應用程式應繫結在執行階段的並排顯示組件的版本。 並排顯示組件資訊清單指定名稱、 版本、 資源和其他組件及其相依性。  
  
 有兩種方式可建立隔離的應用程式或並排顯示組件的資訊清單。 首先，組件的作者，可以手動建立遵循規則，並命名需求的資訊清單檔。 或者，如果程式只相依於 Visual c + + 組件，例如 CRT、 MFC、 ATL 或其他項目，然後將資訊清單可以自動產生連結器。  
  
 Visual c + + 程式庫標頭包含組件的詳細資訊，並當應用程式程式碼中包含程式庫時，連結器會使用此組件資訊來形成最終二進位檔的資訊清單。 連結器不會內嵌於二進位檔，資訊清單檔案，並只會產生做為外部檔案的清單。 將做為外部檔案的資訊清單可能不適用於所有案例。 比方說，建議您使用私用組件有內嵌資訊清單。 在命令列組建，例如使用 nmake 來建置程式碼，資訊清單可以內嵌使用資訊清單的工具;如需詳細資訊，請參閱[在命令列的資訊清單產生](../build/manifest-generation-at-the-command-line.md)。 建置時 Visual Studio 中，您可以內嵌資訊清單設定中的資訊清單工具屬性**專案屬性**對話方塊，請參閱[Visual Studio 中的資訊清單產生](../build/manifest-generation-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [隔離的應用程式和並排顯示組件的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [建置 C/C++ 隔離應用程式和並存組件](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)