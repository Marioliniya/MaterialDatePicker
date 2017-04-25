# MaterialDatePicker

Yet another iOS-based date picker!  This date time picker provides an easy way of creating both single and multi-viewed calendars capable of accepting single, range, and multiple selected dates.  Easy to use. Solved year list issus in this updated calendar

## Quick start

```
Download the latest release

//
//  ViewController.m
//
//  Copyright © 2017 Socialinfotech. All rights reserved.
//

#import "ViewController.h"
#import "NSDate+MDExtension.h"
#import "MDDatePickerDialog.h"

@interface ViewController ()<MDDatePickerDialogDelegate>
@property(weak, nonatomic) IBOutlet UITextField *txtDate;
@property(nonatomic) NSDateFormatter *dateFormatter;

@property(nonatomic) MDDatePickerDialog *datePicker;

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    // Do any additional setup after loading the view, typically from a nib.

    _dateFormatter = [[NSDateFormatter alloc] init];
}


- (IBAction)Click_OpenDatePicker:(id)sender {

  
    if (!_datePicker) {
        NSDateComponents *dateComponents = [[NSDateComponents alloc] init];
        dateComponents.year = 2017;
        dateComponents.month = 4;
        dateComponents.day = 1;
        NSDate *date = [[NSCalendar currentCalendar] dateFromComponents:dateComponents];
        NSDateFormatter *dateFormatter = [[NSDateFormatter alloc] init];
        [dateFormatter setDateFormat:@"yyyy-MM-dd"];

        MDDatePickerDialog *datePicker = [[MDDatePickerDialog alloc] init];
        _datePicker = datePicker;
        _datePicker.disableDates = @[];//Darshit
        _datePicker.disableDatesFormater = dateFormatter;//Darshit
        _datePicker.minimumDate = date;
        _datePicker.selectedDate = date;
        _datePicker.delegate = self;
    }
    [_datePicker show];
}
/* ;
#pragma mark - Navigation
*/

- (void)datePickerDialogDidSelectDate:(NSDate *)date {
    _dateFormatter.dateFormat = @"dd-MM-yyyy";
    _txtDate.text = [_dateFormatter stringFromDate:date];
}



@end
```

## Looks like

<img src="https://raw.githubusercontent.com/fpt-software/Material-Controls-For-iOS/master/Screenshots/MDDatePicker.gif" />
