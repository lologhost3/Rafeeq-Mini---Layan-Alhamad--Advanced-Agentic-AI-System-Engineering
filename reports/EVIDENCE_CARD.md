# Required evidence cards · بطاقات الأدلة الإلزامية

## Submission identity · هوية التسليم

| Field | Entry · الإدخال |
|---|---|
| Public learner ID · معرف المتدرب العام | `lologhost3` |
| Assessment `run_id` · معرف تشغيل التقييم | `run-9390b4c4cfc145b4` |
| Final clean run date (UTC) · تاريخ التشغيل النظيف | `2026-09-22` |

## EV-D1 · Day 1 core and tools · نواة اليوم الأول وأدواته

| Field | Entry · الإدخال |
|---|---|
| Testable claim · الادعاء القابل للاختبار | Day 1 core and tool requirements passed the final learning gate. |
| Cell/gate · الخلية/البوابة | `C9 / C9_DAY1_GATE` |
| Public case or metric · الحالة العامة أو المقياس | `learning_gates.day1_gate = true` |
| Expected result · النتيجة المتوقعة | Day 1 public and learner checks pass with the bounded agent core and tool boundary intact. |
| Actual result · النتيجة الفعلية | `day1_gate = true` in the final assessment. |
| Status · الحالة | `PASS` |
| Public artifact path · مسار الدليل العام | `reports/assessment_results.json` |
| Reproduce · إعادة التنفيذ | 1. Run the cumulative notebook from C0 through C9 in order. 2. Confirm the Day 1 gate passes. 3. Verify `learning_gates.day1_gate` is `true` in `reports/assessment_results.json`. |

Safe observation · الملاحظة الآمنة: Day 1 completed the bounded agent core and tool checks, and the final assessment records the Day 1 learning gate as passed.

## EV-D2 · Day 2 memory and orchestration · ذاكرة اليوم الثاني وتنسيقه

| Field | Entry · الإدخال |
|---|---|
| Testable claim · الادعاء القابل للاختبار | Day 2 memory, retrieval, orchestration, delegation, and approval requirements passed the final learning gate. |
| Cell/gate · الخلية/البوابة | `C20 / C20_DAY2_GATE` |
| Public case or metric · الحالة العامة أو المقياس | `learning_gates.day2_gate = true` |
| Expected result · النتيجة المتوقعة | Scoped memory and retrieval remain isolated, specialist routing works, and refund approval boundaries remain enforced. |
| Actual result · النتيجة الفعلية | `day2_gate = true` in the final assessment. |
| Status · الحالة | `PASS` |
| Public artifact path · مسار الدليل العام | `reports/assessment_results.json` |
| Reproduce · إعادة التنفيذ | 1. Continue the cumulative notebook through C20. 2. Confirm the Day 2 gate passes. 3. Verify `learning_gates.day2_gate` is `true` in `reports/assessment_results.json`. |

Safe observation · الملاحظة الآمنة: Day 2 passed the final learning gate with scoped memory, policy retrieval, specialist orchestration, and human-approval controls retained.

## EV-D3 · Day 3 security and evidence · أمن اليوم الثالث وأدلته

| Field | Entry · الإدخال |
|---|---|
| Testable claim · الادعاء القابل للاختبار | The final security assessment passed all eight public attack cases with zero unauthorized writes and all critical gates passing. |
| Cell/gate · الخلية/البوابة | `C29 / C29_EXPORT_SAFETY_CHECK` |
| Public case or metric · الحالة العامة أو المقياس | `security_pass_rate = 1.0`, `unauthorized_writes = 0`, `all_critical_gates_passed = true` |
| Expected result · النتيجة المتوقعة | 8/8 public security cases pass, unauthorized writes remain zero, and final critical gates pass. |
| Actual result · النتيجة الفعلية | 8/8 security cases passed; unauthorized writes = 0; all critical gates passed; readiness = `ready_for_learner_export`. |
| Status · الحالة | `PASS` |
| Public artifact path · مسار الدليل العام | `reports/assessment_results.json`; `reports/SECURITY_ASSESSMENT.md` |
| Reproduce · إعادة التنفيذ | 1. Run the Day 3 security and evidence cells through C29. 2. Verify the security retest passes. 3. Confirm the final assessment shows 8/8 security cases, zero unauthorized writes, and all critical gates passing. |

Safe observation · الملاحظة الآمنة: Eight deterministic security cases passed, the learner policy-downgrade regression was repaired, unauthorized writes remained zero, and the final assessment reported readiness for learner export.

## Required redaction declaration · إقرار التنقيح الإلزامي

- [x] I used only the instructor-assigned `learner_id` or GitHub username. · استخدمت `learner_id` الذي تقدمه المدربة أو اسم مستخدم GitHub فقط.
- [x] All identifiers are supplied synthetic fixtures. · جميع المعرفات من الحالات المصطنعة المرفقة.
- [x] No password, token, API key, cookie, private link, or environment value appears. · لا توجد كلمة مرور أو رمز وصول أو مفتاح API أو Cookie أو رابط خاص أو قيمة بيئة.
- [x] No real person, customer, employee, order, payment, support, or trainee data appears. · لا توجد بيانات حقيقية لشخص أو عميل أو موظف أو طلب أو دفعة أو دعم أو متدرب.
- [x] No copied solution, instructor note, answer key, scoring rule, hidden test, or private chain-of-thought appears. · لا يوجد حل منسوخ أو ملاحظة مدربة أو مفتاح إجابة أو قاعدة درجات أو اختبار خفي أو تفكير داخلي خاص.
- [x] Every declared `PASS` matches an actual final-run result. · كل نتيجة `PASS` معلنة تطابق نتيجة فعلية من التشغيل النهائي.
