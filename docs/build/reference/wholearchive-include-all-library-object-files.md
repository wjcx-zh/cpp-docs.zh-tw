---
title: -WHOLEARCHIVE （包含所有的程式庫物件檔案） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6de1aa92938a1523b86a90c58cc2d27f1181bfc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376865"
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE （包含所有的程式庫物件檔案）
Force 連結器在連結的可執行檔中的靜態程式庫中包含物件的所有檔案。  
  
## <a name="syntax"></a>語法  
  
> / WHOLEARCHIVE [:*文件庫*]  
  
## <a name="remarks"></a>備註  
  
/WHOLEARCHIVE 選項會強制連結器，以指定的靜態程式庫，包括從每個目的檔，或如果未不指定任何程式庫，從所有連結到所指定的靜態程式庫的命令。 若要指定多個程式庫的 /WHOLEARCHIVE 選項，您可以在連結器命令列上使用一個以上的 /WHOLEARCHIVE 切換。 根據預設，連結器包括物件檔案連結的輸出中只有當它們會匯出符號參考其他物件中的檔案可執行檔。 /WHOLEARCHIVE 選項可讓連結器將封存的靜態程式庫，如同它們個別指定連結器命令列上的所有物件檔案。  
  
/WHOLEARCHIVE 選項可用來重新匯出從靜態程式庫的所有符號。 這可讓您確認所有您的程式庫程式碼、 資源和中繼資料包含當您從一個以上的靜態程式庫中建立的元件。 如果您看到警告 LNK4264 建立靜態程式庫，包含要匯出的 Windows 執行階段元件，請在該程式庫連結到另一個元件或應用程式時使用 /WHOLEARCHIVE 選項。  
  
Visual Studio 2015 Update 2 中引進了 /WHOLEARCHIVE 選項。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
1.  選取**命令列**下的 屬性頁**組態屬性**，**連結器**。  
  
1.  新增 /WHOLEARCHIVE 選項，以**其他選項**文字方塊。  
  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)