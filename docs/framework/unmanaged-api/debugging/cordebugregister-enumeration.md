---
title: CorDebugRegister 열거형
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 85df98e83396c9439c28dd41a3ffa02b820c9c3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726056"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="7fe5e-102">CorDebugRegister 열거형</span><span class="sxs-lookup"><span data-stu-id="7fe5e-102">CorDebugRegister Enumeration</span></span>

<span data-ttu-id="7fe5e-103">지정한 프로세서 아키텍처에 연결된 레지스터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe5e-104">구문</span><span class="sxs-lookup"><span data-stu-id="7fe5e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="7fe5e-105">멤버</span><span class="sxs-lookup"><span data-stu-id="7fe5e-105">Members</span></span>  
  
|<span data-ttu-id="7fe5e-106">멤버</span><span class="sxs-lookup"><span data-stu-id="7fe5e-106">Member</span></span>|<span data-ttu-id="7fe5e-107">설명</span><span class="sxs-lookup"><span data-stu-id="7fe5e-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="7fe5e-108">프로세서의 명령 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="7fe5e-109">프로세서의 스택 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="7fe5e-110">프로세서의 프레임 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="7fe5e-111">x86 프로세서의 명령 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="7fe5e-112">x86 프로세서의 스택 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="7fe5e-113">x86 프로세서의 기본 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="7fe5e-114">x86 프로세서의 A 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="7fe5e-115">x86 프로세서의 C 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="7fe5e-116">x86 프로세서의 D 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="7fe5e-117">x86 프로세서의 B 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="7fe5e-118">x86 프로세서의 소스 인덱스 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="7fe5e-119">x86 프로세서의 대상 인덱스 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="7fe5e-120">x86 FP(부동 소수점) 프로세서의 스택 레지스터 0입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="7fe5e-121">x86 FP 프로세서의 1번 스택 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="7fe5e-122">x86 FP 프로세서의 2번 스택 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="7fe5e-123">x86 FP 프로세서의 3번 스택 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="7fe5e-124">x86 FP 프로세서의 4번 스택 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="7fe5e-125">x86 FP 프로세서의 5번 스택 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="7fe5e-126">x86 FP 프로세서의 6번 스택 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="7fe5e-127">x86 FP 프로세서의 7번 스택 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="7fe5e-128">AMD64 프로세서의 명령 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="7fe5e-129">AMD64 프로세서의 스택 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="7fe5e-130">AMD64 프로세서의 기본 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="7fe5e-131">AMD64 프로세서의 A 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="7fe5e-132">AMD64 프로세서의 C 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="7fe5e-133">AMD64 프로세서의 D 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="7fe5e-134">AMD64 프로세서의 B 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="7fe5e-135">AMD64 프로세서의 소스 인덱스 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="7fe5e-136">AMD64 프로세서의 대상 인덱스 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="7fe5e-137">AMD64 프로세서의 8번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="7fe5e-138">AMD64 프로세서의 9번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="7fe5e-139">AMD64 프로세서의 10번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="7fe5e-140">AMD64 프로세서의 11번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="7fe5e-141">AMD64 프로세서의 12번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="7fe5e-142">AMD64 프로세서의 13번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="7fe5e-143">AMD64 프로세서의 14번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="7fe5e-144">AMD64 프로세서의 15번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="7fe5e-145">AMD64 프로세서의 0번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="7fe5e-146">AMD64 프로세서의 1번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="7fe5e-147">AMD64 프로세서의 2번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="7fe5e-148">AMD64 프로세서의 3번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="7fe5e-149">AMD64 프로세서의 4번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="7fe5e-150">AMD64 프로세서의 5번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="7fe5e-151">AMD64 프로세서의 6번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="7fe5e-152">AMD64 프로세서의 7번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="7fe5e-153">AMD64 프로세서의 8번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="7fe5e-154">AMD64 프로세서의 9번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="7fe5e-155">AMD64 프로세서의 10번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="7fe5e-156">AMD64 프로세서의 11번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="7fe5e-157">AMD64 프로세서의 12번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="7fe5e-158">AMD64 프로세서의 13번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="7fe5e-159">AMD64 프로세서의 14번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="7fe5e-160">AMD64 프로세서의 15번 멀티미디어 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="7fe5e-161">IA-64 프로세서의 스택 포인터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="7fe5e-162">IA-64 프로세서의 0번 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="7fe5e-163">IA-64 프로세서의 0번 FP 데이터 레지스터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="7fe5e-164">ARM 프로세서의 프로그램 카운터 레지스터(R15)입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="7fe5e-165">ARM 프로세서의 스택 포인터 레지스터(R13)입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="7fe5e-166">ARM 프로세서의 데이터 레지스터 R0입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="7fe5e-167">ARM 프로세서의 데이터 레지스터 R1입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="7fe5e-168">ARM 프로세서의 데이터 레지스터 R2입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="7fe5e-169">ARM 프로세서의 데이터 레지스터 R3입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="7fe5e-170">ARM 프로세서의 레지스터 R4입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="7fe5e-171">ARM 프로세서의 레지스터 R5입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="7fe5e-172">ARM 프로세서의 레지스터 R6입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="7fe5e-173">ARM 프로세서의 레지스터 R7(THUMB 프레임 포인터)입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="7fe5e-174">ARM 프로세서의 레지스터 R8입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="7fe5e-175">ARM 프로세서의 레지스터 R9입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="7fe5e-176">ARM 프로세서의 레지스터 R10입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="7fe5e-177">ARM 프로세서의 프레임 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="7fe5e-178">ARM 프로세서의 레지스터 R12입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="7fe5e-179">ARM 프로세서의 링크 레지스터(R14)입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fe5e-180">설명</span><span class="sxs-lookup"><span data-stu-id="7fe5e-180">Remarks</span></span>  

 <span data-ttu-id="7fe5e-181">IA-64 프로세서에는 범용 데이터 레지스터와 부동 소수점 데이터 레지스터가 각각 128개씩 있지만 `REGISTER_IA64_R0` 및 `REGISTER_IA64_F0` 값만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="7fe5e-182">나머지 값은 다음과 같이 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-182">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="7fe5e-183">`REGISTER_IA64_R0`~`REGISTER_IA64_R1` 값의 경우 레지스터 번호를 `REGISTER_IA64_R127`에 더합니다. 그러면 IA-64 프로세서에서 1번~127번 데이터 레지스터에 해당하는 값이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="7fe5e-184">`REGISTER_IA64_F0`~`REGISTER_IA64_F1` 값의 경우 레지스터 번호를 `REGISTER_IA64_F127`에 더합니다. 그러면 IA-64 프로세서에서 1번~127번 FP 데이터 레지스터에 해당하는 값이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="7fe5e-185">예를 들어 IA-64 프로세서의 83번 데이터 레지스터를 지정해야 한다면 `REGISTER_IA64_R0` + 83을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fe5e-186">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7fe5e-186">Requirements</span></span>  

 <span data-ttu-id="7fe5e-187">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7fe5e-187">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fe5e-188">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fe5e-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fe5e-189">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fe5e-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fe5e-190">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fe5e-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe5e-191">참조</span><span class="sxs-lookup"><span data-stu-id="7fe5e-191">See also</span></span>

- [<span data-ttu-id="7fe5e-192">디버깅 열거형</span><span class="sxs-lookup"><span data-stu-id="7fe5e-192">Debugging Enumerations</span></span>](debugging-enumerations.md)
