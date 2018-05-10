---
title: 加入字串的格式或特殊字元 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: c40f394a-8b2c-4896-ab30-6922863ddbb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 429ba8d836579bd3bc1d1dd8844494bf9cd17a7a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="adding-formatting-or-special-characters-to-a-string"></a>將格式或特殊字元加入至字串
### <a name="to-add-formatting-or-special-characters-to-a-string"></a>若要加入格式或特殊字元的字串  
  
1.  開啟字串資料表，其在圖示上按兩下[資源檢視](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  選取您想要修改的字串。  
  
3.  在[屬性 視窗](/visualstudio/ide/reference/properties-window)，新增任何標準逸出序列的下面所列的文字**標題** 方塊中，然後按**ENTER**。  
  
    |若要取得這|輸入下列命令|  
    |-----------------|---------------|  
    |換行|\n|  
    |歸位字元|\r|  
    |索引標籤|\t|  
    |反斜線 (\\)|\\\|  
    |ASCII 字元|\ddd （八進位標記法）|  
    |警示 （鈴聲）|\a|  
  
> [!NOTE]
>  字串編輯器不支援一組完整的逸出的 ASCII 字元。 您只能使用以上所列。  
  
 如需將資源加入至 managed 專案 （其會以 common language runtime 為目標） 的資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中 *.NET Framework 開發人員手冊 》。* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) 和 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 **需求**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [字串編輯器](../windows/string-editor.md)   

