---
title: Microsoft 巨集群組合器 BNF 文法
description: 適用于 x64 之 MASM 的 BNF 描述。
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), BNF reference
ms.openlocfilehash: 1a9577292e60db73838e5e6b850a4634db959fd6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075469"
---
# <a name="microsoft-macro-assembler-bnf-grammar"></a>Microsoft 巨集群組合器 BNF 文法

此頁面包含 MASM 文法的 BNF 描述。 提供參考主題的補充，並不保證會完成。 如需關鍵字、參數、作業等等的完整資訊，請參閱參考主題。

為了說明 BNF 的使用方式，下圖顯示 TYPEDEF 指示詞的定義，從語法*typedefDir*開始。

![MASM BNF 範例](media/bnf.png)

每個水準大括弧下的專案都是可進一步定義的終端機（例如**NEAR16**、 **NEAR32**、 **FAR16**和**FAR32**）或非終端項（例如辨識*符號*、 *qualifiedType*、*距離*和*protoSpec*）。 *TypedefDir*定義中的每個斜體語法也是 BNF 中的專案。 有三個垂直點表示語法的分支定義，為了簡單起見，此圖不會說明。

BNF 文法允許遞迴定義。 例如，文法會使用 qualifiedType 做為 qualifiedType 的可能定義，這也是限定詞定義的元件。 "|" 符號會指定替代運算式之間的選擇，例如*endOfLine* | *comment*。 以雙括弧指定選擇性參數，例如⟦ *macroParmList* ⟧。 括弧實際上不會出現在原始程式碼中。

## <a name="masm-nonterminals"></a>MASM 非終端項

*;;* \
&nbsp;&nbsp;&nbsp;&nbsp;*endOfLine* | *批註*

*= Dir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* = *immExpr* ;;

*addOp*\
&nbsp;&nbsp;&nbsp;&nbsp;+ |-

*aExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*詞彙* | *aExpr* && *詞彙*

*altId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;*charList*

*asmInstruction*\
&nbsp;&nbsp;&nbsp;&nbsp;*助憶鍵*⟦ *exprList* ⟧

*assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**假設** *assumeList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| **假設沒有**;;

*assumeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeRegister* | *assumeList* ， *assumeRegister*\

*assumeReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*register* ： *assumeVal*

*assumeRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeSegReg* | *assumeReg*

*assumeSegReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentRegister* ： *assumeSegVal*

*assumeSegVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*frameExpr* | 不會**發生** **任何**錯誤 | 

*assumeVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | 不會**發生** **任何**錯誤 | 

*bcdConst*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *sign* ⟧ *decNumber*

*binaryOp*\
&nbsp;&nbsp;&nbsp;&nbsp;= = |！ = |> = |< = |> |< |&

*bitDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitFieldId* ： *BitFieldSize* ⟦ = *constExpr* ⟧

*bitDefList*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitDef* | *bitDefList* ，⟦;;⟧ *bitDef*

*bitFieldId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*bitFieldSize*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*blockStatements*\
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。繼續** **。IF** *cExpr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。中斷**⟦ **。如果** *cExpr* ⟧

*bool*\
&nbsp;&nbsp;&nbsp;&nbsp;**TRUE** | **FALSE**

*byteRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AL |AH |CL |CH |DL |DH |BL |BH |R8B |R9B |R10B |R11B |R12B |R13B |R14B |R15B

*cExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*aExpr* | *cExpr* || *aExpr*

*字元*\
&nbsp;&nbsp;&nbsp;&nbsp;範圍介於0到255之間的任何字元，分行符號除外（10）。

*charList*\
&nbsp;&nbsp;&nbsp;&nbsp;*字元* | *charList*字元

*className*\
&nbsp;&nbsp;&nbsp;&nbsp;*字串*

*commDecl*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *nearfar* ⟧⟦ *langType* ⟧ *id* ： *commType*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦： *constExpr* ⟧

*commDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**通訊**\
&nbsp;&nbsp;&nbsp;&nbsp;*commList* ;;

*批註*\
&nbsp;&nbsp;&nbsp;&nbsp;;*text* ;;

*commentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**批註***分隔符號*\
&nbsp;&nbsp;&nbsp;&nbsp;*文字*\
&nbsp;&nbsp;&nbsp;&nbsp;*文字* *分隔符號* *文字*;;

*commList*\
&nbsp;&nbsp;&nbsp;&nbsp;*commDecl* | *commList* ， *commDecl*

*commType*\
&nbsp;&nbsp;&nbsp;&nbsp;*類型* | *constExpr*

*常數*\
&nbsp;&nbsp;&nbsp;&nbsp;*位數*⟦ *radixOverride* ⟧

*constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*coNtextDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**PUSHCONTEXT** *coNtextItemList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;**POPCONTEXT** *coNtextItemList* ;;

*coNtextItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**假設** | 的**基數** | **列出** | **全部**的**CPU** | 

*coNtextItemList*\
&nbsp;&nbsp;&nbsp;&nbsp;*coNtextItem* | *coNtextItemList* ， *coNtextItem*

*controlBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*whileBlock* | *repeatBlock*

*controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*controlIf* | *controlBlock*

*controlElseif*\
&nbsp;&nbsp;&nbsp;&nbsp; **。ELSEIF** &nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧

*controlIf*\
&nbsp;&nbsp;&nbsp;&nbsp; **。如果**&nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlElseif* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **。ELSE** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;[*directiveList*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp; **。ENDIF** ;;

*副處理器*\
&nbsp;&nbsp;&nbsp;&nbsp;. 8087 |. 287 | 387 |。NO87

*crefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*crefOption* ;;

*crefOption*\
&nbsp;&nbsp;&nbsp;&nbsp; **。CREF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.XCREF** ⟦ *idlist.txt* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOCREF** ⟦ *idlist.txt* ⟧

*cxzExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;|！ *expr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* = = expr \
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* ！ = expr

*dataDecl*\
&nbsp;&nbsp;&nbsp;&nbsp;DB |DW |DD |DF |DQ |DT |*dataType* | *typeId*

*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *id* ⟧ *dataItem* ;;

*dataItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDecl* *scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag* *recordInstList*

*dataType*\
&nbsp;&nbsp;&nbsp;&nbsp;位元組 |SBYTE |WORD |寶劍 |DWORD |SDWORD |FWORD |QWORD |SQWORD |TBYTE |OWORD |REAL4 |REAL8 |REAL10 |MMWORD |XMMWORD |YMMWORD

*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;0 |1 |2 |3 |4 |5 |6 |7 |8 |9

*decNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *decNumber* *decdigit*

*分隔符號*\
&nbsp;&nbsp;&nbsp;&nbsp;*whiteSpaceCharacter*以外的任何字元

*數位*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *數位* *decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *數位*hexdigit

指示*詞\*
&nbsp;&nbsp;&nbsp;&nbsp;*generalDir* | *segmentDef*

*directiveList*\
&nbsp;&nbsp; *&nbsp;&nbsp;指示*詞 | *directiveList* *directive*指示詞

*距離*\
&nbsp;&nbsp;&nbsp;&nbsp;*nearfar* | **NEAR16** | **NEAR32** | **FAR16** | **FAR32**

*e01*\
&nbsp;&nbsp;&nbsp;&nbsp;e01 *orOp* *e02* | *e02*

*e02*\
&nbsp;&nbsp;&nbsp;&nbsp;e02**和** *e03* | *e03*

*e03*\
&nbsp;&nbsp;&nbsp;&nbsp;**不** *e04* | *e04*

*e04*\
&nbsp;&nbsp;&nbsp;&nbsp;*e04* *relOp* *e05* | *e05*

*e05*\
&nbsp;&nbsp;&nbsp;&nbsp;*e05* *addOp* *e06* | *e06*

*e06*\
&nbsp;&nbsp;&nbsp;&nbsp;*e06* *mulOp* *e07* | *e06* *shiftOp* *e07* | *e07*

*e07*\
&nbsp;&nbsp;&nbsp;&nbsp;*e07* *addOp* *e08* | *e08*

*e08*\
&nbsp;&nbsp;&nbsp;&nbsp;**高** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **低** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **HIGHWORD** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LOWWORD** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e09*

*e09*\
&nbsp;&nbsp;&nbsp;&nbsp;**OFFSET** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SEG** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LROFFSET** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **類型** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **此** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e09* **PTR** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e09* ： *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e10*

*e10*\
&nbsp;&nbsp;&nbsp;&nbsp;*e10* 。 *e11*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e10* ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *e11*

*e11*\
&nbsp;&nbsp;&nbsp;&nbsp;（ *expr* ） \
&nbsp;&nbsp;&nbsp;&nbsp;|⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **寬度***識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp;| **MASK** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SIZE** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SIZEOF** *sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| **長度***識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LENGTHOF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;| *字串*\
&nbsp;&nbsp;&nbsp;&nbsp;| *常數*\
&nbsp;&nbsp;&nbsp;&nbsp;| *類型*\
&nbsp;&nbsp;&nbsp;&nbsp;| *識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp;| **$**\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;| *register*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ST**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ST** （ *expr* ）

*echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**ECHO**\
&nbsp;&nbsp;&nbsp;&nbsp;*arbitraryText* ;; \
%**OUT** *arbitraryText* ;; \

*elseifBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*elseifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \

*elseifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;**ELSEIF** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIF** *textItem* 、 *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIFI** *textItem* 、 *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDN** *textItem* 、 *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDNI** *textItem* 、 *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF2**

*endDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**END** ⟦ *immExpr* ⟧;;

*endpDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*procId* **ENDP** ;;

*endsDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼***結束**;;

*equDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*textMacroId* **等於** *equType* ;;

*equType*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr* | *textLiteral*

*errorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*errorOpt* ;;

*errorOpt*\
&nbsp;&nbsp;&nbsp;&nbsp; **。ERR** ⟦ *textItem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRE** *constExpr* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRNZ** *constExpr* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRB** *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRNB** *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRDEF** *id* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRNDEF** *id* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRDIF** *textItem* 、 *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRDIFI** *textItem* 、 *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRIDN** *textItem* 、 *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRIDNI** *textItem* 、 *textItem* ⟦ *optText* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERR1** ⟦ *textItem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERR2** ⟦ *textItem* ⟧

*exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。結束 &nbsp;&nbsp;** &nbsp;&nbsp;⟦ *expr* ⟧;;

*exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;： EXITM |EXITM *textItem*

*指數*\
&nbsp;&nbsp;&nbsp;&nbsp;E ⟦ *sign* ⟧ *decNumber*

*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;**SHORT** *e05*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。輸入**e01 \
&nbsp;&nbsp;&nbsp;&nbsp;| **OPATTR** *e01*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e01*

*exprList*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* | *exprList* ， *expr*

*externDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧ *Id* ⟦（ *altId* ）⟧： *externType*

*externDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*externKey* *externList* ;;

*externKey*\
&nbsp;&nbsp;&nbsp;&nbsp;**EXTRN** | **EXTERN** | **EXTERNDEF**

*externList*\
&nbsp;&nbsp;&nbsp;&nbsp;*externDef* | *externList* ，⟦;;⟧ *externDef*

*externType*\
&nbsp;&nbsp;&nbsp;&nbsp;**ABS** | *qualifiedType*

*fieldAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*fieldInit*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *initValue* ⟧ |*structInstance*

*fieldInitList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fieldInit* | *fieldInitList* ，⟦;;⟧ *fieldInit*

*fileChar*\
&nbsp;&nbsp;&nbsp;&nbsp;*分隔符號*

*fileCharList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileChar* | *fileCharList* *fileChar*

*fileSpec*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileCharList* | *textLiteral*

*flagName*\
&nbsp;&nbsp;&nbsp;&nbsp;**零嗎？** | **攜帶嗎？** | **溢位？** | **SIGN？** | 同位檢查**嗎？**

*floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *sign* ⟧ *decNumber* 。 ⟦ *decNumber* ⟧⟦*指數*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *數位*R |*數位*r

*forcDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**FORC** | **IRPC**

*forDir*\
 | **IRP** **的**&nbsp;&nbsp;&nbsp;&nbsp;

*forParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*⟦： *forParmType* ⟧

*forParmType*\
&nbsp;&nbsp;&nbsp;&nbsp;**需求**|= *textLiteral*

*fpuRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**ST** *expr*

*frameExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;**SEG** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **DGROUP** ： *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister* ： *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *識別碼*

*generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelDir* | *segOrderDir* | *nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *includeLibDir* | *commentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *groupDir* | *assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structDir* | *recordDir* | *typedefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *externDir* | *publicDir* | *commDir* | *protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *equDir* |= Dir |*textDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *coNtextDir* | *optionDir* | *processorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *titleDir* | *pageDir* | *listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *crefDir* | *echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ifDir* | *errorDir* | *includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroDir* | *macroCall* | *macroRepeat* | *purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *macroWhile* | *macroFor* | *macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;| *aliasDir*

*gpRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AX |EAX |CX |ECX |DX |EDX |BX |EBX |DI |EDI |SI |ESI |BP |EBP |SP |ESP |.RSP |R8W |R8D |R9W |R9D |R12D |R13W |R13D |R14W |R14D

*groupDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*groupId* **群組** *segIdList*

*groupId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*hexdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;|b |c |d |e |f |A |B |C |D |E |F

*識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp;識別碼的第一個字元可以是大寫或小寫字母字元（`[A–Za-z]`）或這四個字元的任何一個： `@ _ $ ?` 剩餘的字元可以是任何這些相同的字元或十進位數（`[0–9]`）。 長度上限為247個字元。

*idlist.txt*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *idlist.txt* ， *id*

*ifDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **ELSE** ;;\
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* ⟧;; \

*ifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;**如果** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFNB** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFNDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIF** *textItem* 、 *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIFI** *textItem* 、 *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDN** *textItem* 、 *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFIDNI** *textItem* 、 *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF2**

*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*includeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**包含** *fileSpec* ;;

*includeLibDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**INCLUDELIB** *fileSpec* ;;

*initValue*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *字串*\
&nbsp;&nbsp;&nbsp;&nbsp;|？ \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** （ *scalarInstList* ） \
&nbsp;&nbsp;&nbsp;&nbsp;| *floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;| *bcdConst*

*inSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *labelDef* ⟧ *inSegmentDir*

*inSegDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*inSegDir* | *inSegDirList* *inSegDir*

*inSegmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*指示*\
&nbsp;&nbsp;&nbsp;&nbsp;| *dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *controlDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *exitDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *labelDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *procDir* ⟦ *localDirList* *⟧⟦ inSegDirList ⟧ endpDir* *\*
&nbsp;&nbsp;&nbsp;&nbsp;| *invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*

*instrPrefix*\
&nbsp;&nbsp;&nbsp;&nbsp;**REP** | **REPE** | **REPZ** | **REPNE** | **REPNZ** | **鎖定**

*指令*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *instrPrefix* ⟧ *asmInstruction*

*invokeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*register* ：： *register* | *expr* | **ADDR** *expr*

*invokeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**INVOKE** *expr* ⟦，⟦;;⟧ *invokeList* ⟧;;

*invokeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*invokeArg* | *invokeList* ，⟦;;⟧ *invokeArg*

*關鍵字*\
&nbsp;&nbsp;&nbsp;&nbsp;任何保留字。

*keywordList*\
&nbsp;&nbsp;&nbsp;&nbsp;*關鍵字* | *關鍵字* *keywordList*

*labelDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*： |*識別碼*：： |@@:

*labelDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼***標籤** *qualifiedType* ;;

*langType*\
&nbsp;&nbsp;&nbsp;&nbsp;**C** | **PASCAL** | **FORTRAN** | **基本** | **SYSCALL** | **STDCALL**

*listDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*listOption* ;;

*listOption*\
&nbsp;&nbsp;&nbsp;&nbsp; **。清單**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOLIST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.XLIST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOLISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.SFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.TFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTMACROALL** |  **.LALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOLISTMACRO** |  **.SALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTMACRO** |  **.XALL**\

*localDef*\
&nbsp;&nbsp;&nbsp;&nbsp;**本機** *idlist.txt* ;;

*localDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**本機** *parmList* ;;

*localDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*localDir* | *localDirList* *localDir*

*localList*\
&nbsp;&nbsp;&nbsp;&nbsp;*localDef* | *localList* *localDef*

*macroArg*\
 % *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;|%*textMacroId*\
&nbsp;&nbsp;&nbsp;&nbsp;|%*macroFuncId* （ *macroArgList* ） \
&nbsp;&nbsp;&nbsp;&nbsp;| *字串*\
&nbsp;&nbsp;&nbsp;&nbsp;| *arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;|< *arbitraryText* >

*macroArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroArg* | *macroArgList* ， *macroArg*

*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *localList* ⟧ *macroStmtList*

*macroCall*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* *macroArgList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *識別碼*（ *macroArgList* ）

*macroDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* **宏**⟦ *macroParmList* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroFor*\
&nbsp;&nbsp;&nbsp;&nbsp;*forDir* *ForParm* ，< *macroArgList* >;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroForc*\
&nbsp;&nbsp;&nbsp;&nbsp;*forcDir* *id* ， *textLiteral* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroFuncId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroProcId* | *macroFuncId*

*macroIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroId* | *macroIdList* ， *macroId*

*macroLabel*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*macroParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*⟦： *parmType* ⟧

*macroParmList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroParm* | *macroParmList* ，⟦;;⟧ *macroParm*

*macroProcId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*macroRepeat*\
&nbsp;&nbsp;&nbsp;&nbsp;*repeatDir* *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroStmt*\
&nbsp;&nbsp; *&nbsp;&nbsp;指示*詞 \
&nbsp;&nbsp;&nbsp;&nbsp;| *exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;|： *macroLabel*\
&nbsp;&nbsp;&nbsp;&nbsp;| **GOTO**\
&nbsp;&nbsp;&nbsp;&nbsp;*macroLabel*

*macroStmtList*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroStmt* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *macroStmtList* *macroStmt* ;; \

*macroWhile*\
&nbsp;&nbsp;&nbsp;&nbsp;，**但** *constExpr*為;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macroBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;**所有** | **無** | **NOTPUBLIC**

*memOption*\
&nbsp;&nbsp; **&nbsp;&nbsp;** SMALL | **小型** | **MEDIUM** | **COMPACT** | **大型** | **龐大** | **平面**

*助憶鍵*\
&nbsp;&nbsp;&nbsp;&nbsp;的指示名稱。

*modelDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。模型**\
&nbsp;&nbsp;&nbsp;&nbsp;*memOption* ⟦、 *modelOptlist* ⟧、;

*modelOpt*\
&nbsp;&nbsp;&nbsp;&nbsp;*langType* | *stackOption*

*modelOptlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelOpt* | *modelOptlist* ， *modelOpt*

*模組*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *directiveList* ⟧ *endDir*

*mulOp*\
&nbsp;&nbsp;&nbsp;&nbsp;\* |/ |**MOD**

*nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**名稱**\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*;; \

*nearfar*\
&nbsp;&nbsp;&nbsp;&nbsp;**近** | **FAR**

*nestedStruct*\
&nbsp;&nbsp;&nbsp;&nbsp;*structHdr* ⟦ *id* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**結束**;; \

*offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*offsetDirType* ;;

*offsetDirType*\
&nbsp;&nbsp;&nbsp;&nbsp;**甚至** | **組織**的*immExpr* | **對齊**⟦ *constExpr* ⟧

*offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;**群組** | **區段** | **平面**

*oldRecordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ |*oldRecordFieldList* ，⟦ *constExpr* ⟧

*optionDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**選項** *optionList* ;;

*optionItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**CASEMAP** ： *mapType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **DOTNAME** | **NODOTNAME**\
&nbsp;&nbsp;&nbsp;&nbsp;| **模擬器** | **NOEMULATOR**\
&nbsp;&nbsp;&nbsp;&nbsp;| **結尾**： *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **EXPR16** | **EXPR32**\
&nbsp;&nbsp;&nbsp;&nbsp;| **語言**： *langType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LJMP**
| **NOLJMP**\
&nbsp;&nbsp;&nbsp;&nbsp;| **M510** | **NOM510**\
&nbsp;&nbsp;&nbsp;&nbsp;| **NOKEYWORD** ： < *keywordList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| **NOSIGNEXTEND**\
&nbsp;&nbsp;&nbsp;&nbsp;| **位移**： *offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDMACROS** | **NOOLDMACROS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **OLDSTRUCTS** | **NOOLDSTRUCTS**\
&nbsp;&nbsp;&nbsp;&nbsp;| **PROC** ： *oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;| **序言**： *macroId*\
&nbsp;&nbsp;&nbsp;&nbsp;| **READONLY** | **NOREADONLY**\
&nbsp;&nbsp;&nbsp;&nbsp;| **範圍** | **NOSCOPED**\
&nbsp;&nbsp;&nbsp;&nbsp;| **區段**： *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SETIF2** ： bool

*optionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*optionItem* | *optionList* ，⟦;;⟧ *optionItem*

*optText*\
&nbsp;&nbsp;&nbsp;&nbsp;、 *textItem*

*orOp*\
&nbsp;&nbsp;&nbsp;&nbsp;**或** | **XOR**

*oVisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;**公用** | **私**用 | **匯出**

*pageDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**頁面**⟦ *pageExpr* ⟧;;

*pageExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;\+ |⟦ *pageLength* ⟧⟦， *pageWidth* ⟧

*pageLength*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*pageWidth*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*parm*\
&nbsp;&nbsp;&nbsp;&nbsp;*parmId* ⟦： *qualifiedType* ⟧ |*parmId* ⟦ *constExpr* ⟧⟦： *qualifiedType* ⟧

*parmId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*parmList*\
&nbsp;&nbsp;&nbsp;&nbsp;*parm* | *parmList* ，⟦;;⟧ *parm*

*parmType*\
&nbsp;&nbsp;&nbsp;&nbsp;**需求**|= *textLiteral* | **VARARG**

*pOptions*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦*距離*⟧⟦ *langType* *⟧⟦ oVisibility* ⟧

*主要*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* *BinaryOp* *expr* | *flagName* | *expr*

*procDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*procId* **PROC**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *pOptions* ⟧⟦ < *macroArgList* > ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *usesRegs* ⟧⟦ *procParmList* ⟧

*處理器*\
&nbsp;&nbsp;&nbsp;&nbsp;|. 386 |. .386p |. 486 |. .486P \
&nbsp;&nbsp;&nbsp;&nbsp;|. 586 |. .586P |. 686 |. .686P |. 387

*processorDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*處理器*;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *副處理器*;;

*procId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*procItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*instrPrefix* | *dataDir* | *labelDir* | *offsetDir* | *generalDir*

*procParmList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦，⟦;;⟧ *parmList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦，⟦;;⟧ *parmId* ： VARARG ⟧

*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *id* ⟧： *qualifiedType*

*protoArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦，⟦;;⟧ *protoList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦，⟦;;⟧⟦ *id* ⟧： VARARG ⟧

*protoList*\
&nbsp;&nbsp;&nbsp;&nbsp;*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *protoList* ，⟦;;⟧ *protoArg*

*protoSpec*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦*距離*⟧⟦ *langType* ⟧⟦ *protoArgList ⟧ |* *typeId*

*protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼* **PROTO** *protoSpec*

*pubDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧*識別碼*

*publicDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**公用** *pubList* ;;

*pubList*\
&nbsp;&nbsp;&nbsp;&nbsp;*pubDef* | *pubList* ，⟦;;⟧ *pubDef*

*purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**清除** *macroIdList*

*qualifiedType*\
&nbsp;&nbsp;&nbsp;&nbsp;*類型*|⟦*距離*⟧ **PTR** ⟦ *qualifiedType* ⟧

辨識*符號*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **PROTO** *protoSpec*

*報價*\
&nbsp;&nbsp;&nbsp;&nbsp;"| '

*qwordRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;RAX |RCX |RDX |RBX |RDI |RSI |RBP |R8 |R9 |R10 |R11 |R12 |R13 |R14 |R15

*radixDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。基數** *constExpr* ;;

*radixOverride*\
&nbsp;&nbsp;&nbsp;&nbsp;h |o |問 |t |y |H |O |問 |T |Y

*recordConst*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* { *oldRecordFieldList* } |*recordTag* < *oldRecordFieldList* >

*recordDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordTag* **記錄** *bitDefList* ;;

*recordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ |*recordFieldList* 、⟦、;⟧⟦ *constExpr* ⟧

*recordInstance*\
 {⟦;; ⟧ *recordFieldList* ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;|< *oldRecordFieldList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** （ *recordInstance* ）

*recordInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordInstance* | *recordInstList* ，⟦;;⟧ *recordInstance*

*recordTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*註冊*\
&nbsp;&nbsp;&nbsp;&nbsp;*specialRegister* | *gpRegister* | *byteRegister* | *qwordRegister* |  *fpuRegister* | *SIMDRegister* | *segmentRegister*

*regList*\
&nbsp;&nbsp;&nbsp;&nbsp;*註冊* | *regList* *register*

*relOp*\
&nbsp;&nbsp;&nbsp;&nbsp;EQ |NE |LT |LE |GT |串聯

*repeatBlock*\
&nbsp;&nbsp;&nbsp;&nbsp; **。重複**;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;;untilDir ;;

*repeatDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**重複** | **REPT**

*scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*initValue* | *scalarInstList* ，⟦;;⟧ *initValue*

*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;**位元組** | **WORD** | **DWORD** | **段落** | **頁面**

*segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;**公用** | **堆疊** | **在** *ConstExpr* | **私**用的**一般** | **記憶體** | 

*segDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。程式碼**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。資料**\
&nbsp;&nbsp;&nbsp;&nbsp;|   **。資料？** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。CONST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。FARDATA**⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|   **。FARDATA？** ⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。STACK** ⟦ *constExpr* ⟧

*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*segIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segIdList* ， *segId*

*segmentDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentDir* ⟦ *inSegDirList* ⟧ *endsDir* | *simpleSegDir* ⟦ *inSegDirList* ⟧⟦ *endsDir* ⟧

*segmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId* **區段**⟦ *segOptionList* ⟧;;

*segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**CS** | **DS** | **ES** | **FS** | **GS** | **SS**

*segOption*\
&nbsp;&nbsp;&nbsp;&nbsp;*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| *className*

*segOptionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segOption* | *segOptionList* *segOption*

*segOrderDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。ALPHA** |  **。SEQ** |  **.DOSSEG** |  **.dosseg**

*segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;**READONLY**

*segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;**USE16** | **USE32** | 簡**維**

*shiftOp*\
&nbsp;&nbsp;&nbsp;&nbsp;**SHR** | **SHL**

*簽署*\
 - |+

*simdRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;MM0 |MM1 |MM2 |MM3 |MM4 |MM5 |MM6 |MM7 |xmmRegister |YMM0 |YMM1 |YMM2 |YMM3 |YMM4 |YMM5 |YMM6 |YMM7 |YMM8 |YMM9 |YMM10 |YMM11 |YMM12 |YMM13 |YMM14 |YMM15

*simpleExpr*\
 （ *cExpr* ） |*主要*

*simpleSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segDir* ;;

*sizeArg*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼* | *類型* | *e10*

*specialChars*\
 : | . |⟦ |⟧ |( | )|< |> |{ | }\
&nbsp;&nbsp;&nbsp;&nbsp;|+ |- |/ |* |&AMP; |% | !\
&nbsp;&nbsp;&nbsp;&nbsp;|' |\ |= | ; |, |"\
&nbsp;&nbsp;&nbsp;&nbsp;| *whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;| *endOfLine*

*specialRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;CR0 暫存器 |CR2 |CR3 |DR0 |DR1 |DR2 |DR3 |DR6 |DR7 |TR3 |TR4 |TR5 |TR6 |TR7

*stackOption*\
&nbsp;&nbsp;&nbsp;&nbsp;**NEARSTACK** | **FARSTACK**

*startupDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。啟動**;;

*stext*\
&nbsp;&nbsp;&nbsp;&nbsp;*stringChar* | *stext* *stringChar*

*string*\
&nbsp;&nbsp;&nbsp;&nbsp;*報價*⟦ *stext* ⟧*報價*

*stringChar*\
&nbsp;&nbsp;&nbsp;&nbsp;*引號* *|* 引號以外的任何字元。

*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structItem* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *structBody* *structItem* ;;

*structDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag* *structHdr* ⟦ *fieldAlign* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦、非**唯一**⟧、、\
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;**結束**;;

*structHdr*\
&nbsp;&nbsp;&nbsp;&nbsp;**STRUC** | **結構** | 聯**集**

*structInstance*\
 < ⟦ *fieldInitList* ⟧ > \
&nbsp;&nbsp;&nbsp;&nbsp;|{⟦;; ⟧⟦ *fieldInitList* ⟧⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** （ *structInstList* ） \

*structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*structInstance* | *structInstList* ，⟦;;⟧ *structInstance*

*structItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generalDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *nestedStruct*

*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*詞彙*\
&nbsp;&nbsp;&nbsp;&nbsp;*simpleExpr* |！ *simpleExpr*

*text*\
&nbsp;&nbsp;&nbsp;&nbsp;*textLiteral* | *文字*字元 |！ *字元* *文字* | *字元*|！*字元*

*textDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼* *textMacroDir* ;;

*textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*textLiteral* | *textMacroId* |% *constExpr*

*textLen*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*textList*\
&nbsp;&nbsp;&nbsp;&nbsp;*textItem* | *textList* ，⟦;;⟧ *textItem*

*textLiteral*\
&nbsp;&nbsp;&nbsp;&nbsp;< *文字*>;;

*textMacroDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**CATSTR** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **TEXTEQU** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **SIZESTR** *textItem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SUBSTR** *textItem* 、 *textStart* ⟦、 *textLen* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **INSTR** ⟦ *TextStart* 、⟧ *textItem* 、 *textItem*

*textMacroId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*textStart*\
&nbsp;&nbsp;&nbsp;&nbsp;*constExpr*

*titleDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*titleType* *arbitraryText* ;;

*titleType*\
&nbsp;&nbsp;&nbsp;&nbsp;**標題** | **副標題** | **SUBTTL**

*類型*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *距離*\
&nbsp;&nbsp;&nbsp;&nbsp;| *dataType*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId*

*typedefDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*typeId* **TYPEDEF**限定詞

*typeId*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*

*untilDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。直到** *cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **.UNTILCXZ** ⟦ *cxzExpr* ⟧;;

*usesRegs*\
&nbsp;&nbsp;&nbsp;&nbsp;**使用** *regList*

*whileBlock*\
&nbsp;&nbsp;&nbsp;&nbsp; **。WHILE**\
&nbsp;&nbsp;&nbsp;&nbsp;*cExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockStatements* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **.ENDW**

*whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;ASCII 8、9、11–13、26、32

*xmmRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;XMM0 |XMM1 |XMM2 |XMM3 |XMM4 |XMM5 |XMM6 |XMM7 |XMM8 |XMM9 |XMM10 |XMM11 |XMM12 |XMM13 |XMM14 |XMM15\
