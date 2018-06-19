---
title: 變更符號標頭檔的名稱 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.header
dev_langs:
- C++
helpviewer_keywords:
- resource files, multiple
- Resource Includes dialog box
- symbol header files, changing names
- symbol header files
- header files, changing names
- names [C++], symbol header files
- symbols, symbol header files
- Resource.h
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 953ac59958748bd58fa7e9027c595bf7905e5f27
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864225"
---
# <a name="changing-the-names-of-symbol-header-files"></a>變更符號標頭檔的名稱
通常會在 Resource.h 中儲存所有符號定義。 不過，您可能需要變更這 Include 檔案名稱，好讓您可以，比方說在相同目錄中處理多個資源檔。  
  
### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>變更資源符號標頭檔名稱  
  
1.  在[資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇  [Resource Includes](../windows/resource-includes-dialog-box.md)從捷徑功能表。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在**符號標頭檔**方塊中，輸入 include 檔的新名稱。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。*  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [檢視資源符號](../windows/viewing-resource-symbols.md)   
 [預先定義的符號識別碼](../windows/predefined-symbol-ids.md)