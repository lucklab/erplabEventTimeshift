# erplab_event_timeshift
ERPLAB function to shift the time of specific event codes given by the user.

#### Purpose

There exists ~20 ms delay between an event code and the onset of the LCD screen. We want to correct this delay, by shifting the stimulus-event codes later in time. All other event codes not specified by the user are kept at their original timepoints. 


#### Input
- Continuous EEG dataset
- List of event codes to shift
- How much time to shift the event codes
- Method for rounding
  - floor
  - ceiling
  - nearest
- Warning flags for event codes that we unable to be shift (for various reasons)

#### Output
- Continuous EEG dataset with the user-specified event codes shifted

#### Example
```matlab
eventcodes = {'22', '19'};
timeshift  = 0.015;
rounding   = 'floor';
outputEEG  = erplab_shiftevents_eeg(inputEEG, eventcodes, timeshift, rounding);
```

----
### Previous Research 

- Related ERPLAB functions `erptimeshift.m` & `eegtimeshift.m`
- [EEGLAB Forums: Event code shifting](http://sccn.ucsd.edu/pipermail/eeglablist/2006/001534.html)
 
> I was wondering whether there is a possibility in eeglab to shift all
> event markers by 50 ms backwards in time?
 ```Matlab
 for index = 1:length(EEG.event)
    EEG.event(index).latency = EEG.event(index).latency-0.05*srate;
end;
EEG = eeg_checkset(EEG, 'eventconsistency'); % check for out of bound events [ALLEEG EEG] = eeg_store(ALLEEG, EEG, CURRENTSET); % store dataset in ALLEEG eeglab redraw; % redraw GUI
```
