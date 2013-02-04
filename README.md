UIComponentDemo
===============


UI components demo project
```
- (void)qaLocationRequest:(NSNotification *)notification {
    if (!self.qaUserLocation)
        return;
    
    NSString *latStr = [NSString stringWithFormat:@"%.4f", self.qaUserLocation.coordinate.latitude];
    NSString *lngStr = [NSString stringWithFormat:@"%.4f", self.qaUserLocation.coordinate.longitude];
    NSDictionary *userInfo = @{@"name":@"QACommandGetUserLocation", @"lat":latStr, @"lng":lngStr};
    
    [[NSNotificationCenter defaultCenter] postNotificationName:@"QACommandResponseMessage" object:nil userInfo:userInfo];
}

- (void)qaLocationChanged:(NSNotification *)notification {
    NSDictionary *userInfo = notification.userInfo;
    CGFloat lat = [[userInfo objectForKey:@"lat"] floatValue];
    CGFloat lng = [[userInfo objectForKey:@"lng"] floatValue];
    self.qaUserLocation = [[CLLocation alloc] initWithLatitude:lat longitude:lng];
}
```
