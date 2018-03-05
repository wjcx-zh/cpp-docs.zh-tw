---
title: "-驗證-字元集 （驗證相容的字元） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /validate-charset
- validate-charset
dev_langs:
- C++
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7694eb94fe1b50d1892dab399b523a5b0e6deef7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate-charset （驗證相容的字元）
驗證的原始程式檔文字只包含字元可表示為 utf-8。  
  
## <a name="syntax"></a>語法  
  
```  
/validate-charset[-]  
```  
  
## <a name="remarks"></a>備註  
 您可以使用**/validate-charset**選項，以驗證您的原始程式碼包含只可以用來表示這兩個來源字元集的字元設定和執行字元集。 當您指定這項檢查會自動啟用**/source-charset**， **/execution-charset**，或**/utf-8**編譯器選項。 您可以藉由指定明確停用這項檢查**/ 驗證-charset-**選項。  
  
 根據預設，Visual Studio 會偵測來判斷來源檔案是否已編碼的 Unicode 格式，例如，utf-8 或 utf-16 位元組順序標記。 如果找到沒有位元組順序標記，它會假設來源檔案編碼使用目前使用者的字碼頁，除非您指定的字碼頁使用**/utf-8**或**/source-charset**選項。 Visual Studio 可讓您使用數種字元編碼的任何儲存您的 c + + 程式碼。 來源和執行字元集的相關資訊，請參閱[字元集](../../cpp/character-sets2.md)語言文件中。 一份支援程式碼頁面識別碼和字元集的名稱，請參閱[程式碼頁面識別碼](http://msdn.microsoft.com/library/windows/desktop/dd317756)。  
  
 Visual Studio 會使用 utf-8，做為來源字元集和執行字元集之間轉換期間的內部字元編碼。 如果原始程式檔中的字元不能以執行字元集來表示，utf-8 轉換取代問號 '？ ' 字元。 **/Validate-charset**選項會使編譯如果發生這種情況會報告警告。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**， **C/c + +**，**命令列**資料夾。  
  
3.  在**進階選項**，新增**/validate-charset**選項，並指定您的慣用編碼方式。  
  
4.  選擇**確定**以儲存變更。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [/execution-charset (設定執行 Character Set)](../../build/reference/execution-charset-set-execution-character-set.md)   
 [/source-charset (設定來源 Character Set)](../../build/reference/source-charset-set-source-character-set.md)   
 [/utf-8 （設定來源和可執行檔字元集為 utf-8）](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)