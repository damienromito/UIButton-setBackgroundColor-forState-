# UIButton setBackgroundColor:forState:

An Objective-c Category to add the method  setBackgroundColor:forState: to the UIButton

**UIButton+BackgroundColor.h**

    @interface UIButton(BackgroundColor)
    - (void)setBackgroundColor:(UIColor *)color forState:(UIControlState)state;
    @end


**UIButton+BackgroundColor.m**

    #import "UIButton+BackgroundColor.h"

    @implementation UIButton(BackgroundColor)

    - (void)setBackgroundColor:(UIColor *)color forState:(UIControlState)state
    {
        [self setBackgroundImage:[self imageWithColor:color] forState:state];
    }

    - (UIImage *)imageWithColor:(UIColor *)color {
        CGRect rect = CGRectMake(0.0f, 0.0f, 1.0f, 1.0f);
        UIGraphicsBeginImageContext(rect.size);
        CGContextRef context = UIGraphicsGetCurrentContext();
        
        CGContextSetFillColorWithColor(context, [color CGColor]);
        CGContextFillRect(context, rect);
        
        UIImage *image = UIGraphicsGetImageFromCurrentImageContext();
        UIGraphicsEndImageContext();
        
        return image;
    }

@end