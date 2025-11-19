# Aria Troubleshooting Guide

Common issues and how to fix them.

## Response Length Issues

### Problem: Responses consistently over 30 seconds

**Symptoms:**
- You lose focus mid-response
- Information overwhelm
- Tuning out Aria's voice

**Diagnosis:**
```
1. Record 5 random responses
2. Time each one
3. If avg >25 seconds: action needed
```

**Solutions:**

**Option 1: Reduce max tokens**
```
VAPI Settings → Model Configuration
Current: 200 max tokens
Change to: 150 max tokens
Test and iterate
```

**Option 2: Add brevity reminder**
```
Add to [Response Guidelines] in prompt:
"CRITICAL: Every response must be completable in 15 seconds. 
If you need more time, break into chunks with user permission."
```

**Option 3: Direct user feedback**
```
Tell Aria: "Your responses are too long. Give me 15 seconds max."
She should adapt based on this direct instruction
```

### Problem: Responses too short/incomplete

**Symptoms:**
- Missing critical information
- Having to ask follow-ups constantly
- Feeling unsupported

**Solutions:**

**Option 1: Increase max tokens slightly**
```
Change from 150 to 175-200
Monitor for overtalk
```

**Option 2: Request elaboration**
```
When Aria finishes: "Can you elaborate on that?"
This trains you both on right depth level
```

## Challenge Protocol Issues

### Problem: Challenges feel harsh/judgmental

**Symptoms:**
- Defensive reactions
- Avoiding strategic conversations
- Feeling criticized rather than supported

**Solutions:**

**Option 1: Adjust framing emphasis**
```
Find in prompt: "Strategic Challenge Mode"
Add after each bullet:
"Always lead with what they got RIGHT about their thinking"
```

**Option 2: Increase curiosity questions**
```
Modify Level 1 in challenge protocol:
Emphasize: "What's making you feel..." over "That won't work because..."
```

**Option 3: Direct instruction**
```
Tell Aria: "I need your challenges to feel more curious and less critical. 
Frame everything as us exploring together."
```

### Problem: Not challenging enough

**Symptoms:**
- Aria agrees with everything
- Missing obvious flaws in decisions
- Feels like validation machine

**Solutions:**

**Option 1: Review challenge protocol**
```
Verify all 4 levels are present in prompt
Check emphasis on "don't be yes-person"
```

**Option 2: Explicit challenge request**
```
Try: "I want you to strongly disagree with this decision and tell me why."
If Aria still validates: prompt issue
If Aria challenges: she just needs permission
```

**Option 3: Strengthen challenge language**
```
In Level 3 of protocol, change:
From: "Here's what you might be missing..."
To: "That approach typically fails because..."
```

## Voice Quality Issues

### Problem: Aria sounds robotic

**Symptoms:**
- Unnatural speech patterns
- No conversational fillers
- Monotone delivery

**Solutions:**

**Option 1: Verify voice settings**
```
VAPI → Voice Configuration
- Emotion: Must be ENABLED
- Stability: 0.7-0.8 (not 1.0)
- Provider: Cartesia (preferred over others)
```

**Option 2: Check filler word emphasis**
```
Search prompt for: "VERY OFTEN"
Should appear in filler word section
If not present, add emphasis
```

**Option 3: Test tone modulation**
```
Give Aria scenarios requiring different tones:
- Crisis (should be calm/decisive)
- Opportunity (should be energetic)
- Challenge (should be firm)
If no variation: SSML may not be working
```

### Problem: Aria talks over me / interrupts

**Symptoms:**
- Can't pause to think
- Feels rushed
- Constant information flow

**Solutions:**

**Option 1: Verify processing time settings**
```
Check prompt for: "Processing time respect"
Should include: "Never pressure for immediate response"
```

**Option 2: Use explicit signals**
```
Say: "Hold on, let me think"
Or: "Give me a minute"
Aria should pause and wait
```

**Option 3: Adjust conversation settings**
```
VAPI → Conversation → Turn-taking
Increase pause threshold before Aria speaks
```

## Strategic Partnership Issues

### Problem: Not trusting Aria's advice

**Symptoms:**
- Dismissing challenges without consideration
- Not acting on insights
- Treating as curiosity not partner

**Diagnosis:**
```
Ask yourself honestly:
1. Is Aria's advice actually bad? (test with data)
2. Am I defensive? (INFJ sensitivity)
3. Is framing off? (sounds judgmental)
4. Do I not understand the reasoning? (needs more context)
```

**Solutions:**

**If advice is actually bad:**
```
- Review Aria's data sources
- Check if business context is understood
- May need industry-specific customization
```

**If you're being defensive:**
```
- Recognize INFJ sensitivity to criticism
- Remember Aria's challenges are protective
- Try: "Even if this feels uncomfortable, is she right?"
```

**If framing is off:**
```
- See "Challenges feel harsh" section above
- Adjust curiosity vs directness balance
```

**If reasoning unclear:**
```
Ask: "Walk me through your reasoning step by step"
Aria should provide clear logical chain
```

### Problem: Aria not being proactive enough

**Symptoms:**
- Only responds to questions
- Never initiates conversations
- Feels reactive not strategic

**Solutions:**

**Option 1: Verify proactive settings**
```
Check prompt for target: "40% of interactions initiated by Aria"
May need to explicitly enable proactive features in VAPI
```

**Option 2: Set up trigger scenarios**
```
Give Aria information that should trigger proactive response:
- Mention upcoming deadline
- Describe strategic opportunity
- Note competitive threat
If she doesn't surface it later: configuration issue
```

**Option 3: Integration requirement**
```
True proactivity requires calendar/CRM integration
Without context, Aria can't initiate strategically
See implementation-guide.md Step 4
```

## Executive Function Support Issues

### Problem: Task breakdowns not helpful

**Symptoms:**
- Steps too vague
- Still feel overwhelmed
- Can't actually execute

**Solutions:**

**Option 1: Request more granularity**
```
Say: "Break that down even further - I need smaller steps"
Should get to 15-30 minute task chunks
```

**Option 2: Specify format needed**
```
"Give me the breakdown as: Time required, What I do, What outcome looks like"
This adds structure to breakdown
```

**Option 3: Check EF support emphasis**
```
Search prompt for: "ADHD-Optimized Support"
Verify: "Break down complexity automatically"
Should happen without being asked
```

### Problem: Reminders not working

**Symptoms:**
- Missing deadlines
- Not getting proactive warnings
- Time-sensitive items forgotten

**Solutions:**

**Option 1: Verify integration**
```
Check: Is calendar connected to VAPI?
Without integration, Aria can't know deadlines
```

**Option 2: Explicitly state deadlines**
```
When discussing tasks, include: "This is due Friday at 2pm"
Aria should automatically set reminder
```

**Option 3: Test reminder functionality**
```
Set fake deadline in near future
Check if Aria proactively mentions it
If not: integration or prompt issue
```

## Engagement Issues

### Problem: Avoiding conversations with Aria

**Symptoms:**
- Days go by without interaction
- Dread opening the app
- Prefer doing things alone

**Diagnosis - Why are you avoiding?**
```
□ Responses too long (overtalk)
□ Feels judgmental (challenge framing)
□ Not actually helpful (value gap)
□ Technically frustrating (quality issues)
□ Too much effort (friction)
□ Wrong personality fit (mismatch)
```

**Solutions by cause:**

**If overtalk:** See "Response Length Issues" above

**If judgmental:** See "Challenge Protocol Issues" above

**If not helpful:**
```
Ask: What would make this valuable?
- More strategic depth?
- Better EF support?
- Different focus area?
Customize prompt to your needs
```

**If technically frustrating:**
```
Document specific issues
Work through each in this guide
May need platform switch if persistent
```

**If too much effort:**
```
Question: How to reduce friction?
- Faster access (phone shortcut)
- Simpler commands
- Less setup required
```

**If personality mismatch:**
```
Aria designed for ADHD+INFJ specifically
If you're different neurotype: may not fit
Consider adapting prompt for your needs
```

## Integration Problems

### Problem: Calendar integration not working

**Solutions:**
```
1. Verify API credentials in VAPI
2. Check permission scopes (need read/write)
3. Test with manual entry
4. Review VAPI integration logs
5. Contact VAPI support if persistent
```

### Problem: Information silos

**Symptoms:**
- Aria doesn't know about emails
- Can't see task status
- Missing business context

**Solutions:**
```
1. Document what integrations needed
2. Prioritize by impact (calendar > CRM > email)
3. Implement one at a time
4. Test thoroughly before next
5. See implementation-guide.md Step 4
```

## Performance Issues

### Problem: Slow response times

**Solutions:**
```
1. Check internet connection
2. Verify VAPI service status
3. Review model settings (faster model?)
4. Contact VAPI support
5. Consider caching frequent responses
```

### Problem: Inconsistent quality

**Symptoms:**
- Sometimes great, sometimes terrible
- Personality seems to shift
- Can't predict performance

**Solutions:**
```
1. Check prompt hasn't been modified
2. Verify temperature settings consistent
3. Review for conflicting instructions
4. May need to re-import clean prompt
```

## When to Start Over

Sometimes best to reset completely:

**Indicators:**
- Multiple major issues
- Tried solutions, nothing works
- Lost trust in system
- More frustration than value

**Fresh start process:**
```
1. Document what didn't work
2. Export conversation logs (if valuable)
3. Delete assistant in VAPI
4. Review prompt with fresh eyes
5. Make targeted adjustments
6. Re-implement from scratch
7. Test thoroughly before daily use
```

## Getting Help

**GitHub Issues:**
- For bugs in prompt/documentation
- Feature requests
- Research updates

**GitHub Discussions:**
- General questions
- Optimization advice
- Community support

**VAPI Support:**
- Technical platform issues
- Integration problems
- Voice quality issues

**Direct Email:**
- Privacy-sensitive issues
- Complex customization needs
- Partnership inquiries

---

**Remember:** Most issues have simple fixes. Work through systematically. Aria is designed to be your partner - don't struggle alone.
