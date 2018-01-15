---
title: "-核心 (建立核心模式二進位檔) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /kernel
- /kernel-
dev_langs: C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0e20df59788577acb680cbd18b737f7ec2d7822
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (建立核心模式二進位檔)
建立可以在 Windows 核心中執行的二進位檔。  
  
## <a name="syntax"></a>語法  
  
```  
/kernel[-]  
```  
  
## <a name="arguments"></a>引數  
 **/kernel**  
 目前的專案中的程式碼編譯，並使用一組專屬於會在核心模式中執行的程式碼的 c + + 語言規則連結。  
  
 **/kernel-**  
 目前的專案中的程式碼編譯及連結而不使用專屬於會在核心模式中執行的程式碼的 c + + 語言規則。  
  
## <a name="remarks"></a>備註  
 沒有任何`#pragma`相當於控制這個選項。  
  
 指定**/kernel**選項會告訴編譯器和連結器在裡頭仲裁哪一個語言功能為允許在核心模式中，並請確定您有足夠的表達能力，以避免執行階段不穩定的核心模式 c + + 所特有。 這是禁止使用干擾核心模式中的 c + + 語言功能以及提供的 c + + 語言功能可能會干擾性，但不能停用警告。  
  
 **/Kernel**選項適用於編譯器和連結器在建置階段，並且設定專案層級。 傳遞**/kernel**參數; 代表編譯器，產生的二進位檔之後連結時，應載入 Windows 核心。 編譯器會縮小範圍廣泛的 c + + 語言功能與核心相容的子集合。  
  
 下表列出編譯器行為的變更時**/kernel**指定。  
  
|行為型別|**/kernel**行為|  
|-------------------|---------------------------|  
|C++ 例外狀況處理|已停用。 所有執行個體`throw`和`try`關鍵字發出編譯器錯誤 (除了例外狀況規格`throw()`)。 否**/EH**選項為相容於**/kernel**，除了**/EH-**。|  
|RTTI|已停用。 所有執行個體`dynamic_cast`和`typeid`關鍵字會發出編譯器錯誤，除非`dynamic_cast`以靜態方式使用。|  
|`new` 和 `delete`|您必須明確地定義`new()`或`delete()`運算子; 編譯器都執行階段會提供預設定義。|  
  
 自訂呼叫慣例， [/GS](../../build/reference/gs-buffer-security-check.md)當您使用允許的組建選項，與所有最佳化**/kernel**選項。 內嵌大多不會受到**/kernel**，利用相同的語意，編譯器接受。 如果您想要確定`__forceinline`內嵌的限定詞會被接受，您必須確定該警告[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)會啟用，因此您知道某一特定`__forceinline`函式不是內嵌。  
  
 當傳遞編譯器**/kernel**參數，它會預先定義前置處理器巨集名為`_KERNEL_MODE`且具有值**1**。 您可以使用這有條件地編譯程式碼，根據是否在使用者模式或核心模式中執行環境。 例如，下列程式碼會指定類別應該位在非可分頁記憶體區段中編譯的核心模式執行時。  
  
```cpp  
#ifdef _KERNEL_MODE  
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))  
#else  
#define NONPAGESECTION  
#endif  
  
class NONPAGESECTION MyNonPagedClass  
{  
   // ...
};  
```  
  
 某些目標架構的下列組合和**/arch**選項搭配使用時，產生錯誤**/kernel**:  
  
-   **/arch: {SSE &#124;SSE2 &#124;AVX}**不支援在 x86 上。 只有**/arch:IA32**支援**/kernel** x86 上。  
  
-   **/arch: avx**不支援**/kernel** x64 上。  
  
 使用建置**/kernel**也會傳遞**/kernel**至連結器。 她是這會連結器行為的影響：  
  
-   已停用累加連結。 如果您將加入**/ 增量**命令列中，連結器會發出這個嚴重錯誤：  
  
     **連結： 嚴重錯誤 LNK1295: '/ 增量' 不相容的 '/ 核心' 規格;沒有 '/ 增量' 連結**  
  
-   連結器會檢查每個目的檔 （或任何包含的封存成員從靜態程式庫） 若要查看是否它可能已編譯使用**/kernel**但未選項。 如果任何執行個體符合此準則，連結器仍已成功連結，但可能會發出警告下, 表所示。  
  
    ||**/kernel** obj|**/kernel-** obj MASM obj 或 cvtresed|混合的**/kernel**和**/kernel-** objs|  
    |-|----------------------|-----------------------------------------------|-------------------------------------------------|  
    |**連結 /kernel**|[是]|[是]|是，但有警告 LNK4257|  
    |**連結**|[是]|是|[是]|  
  
     **不是使用 /KERNEL; 編譯 LNK4257 連結物件映像可能無法執行**  
  
 **/Kernel**選項和**/driver**選項是獨立運作，並且兩者都不會影響其他。  
  
### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定 /kernel 編譯器選項  
  
1.  開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  在**其他選項**方塊中，加入`/kernel`或`/kernel-`。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)