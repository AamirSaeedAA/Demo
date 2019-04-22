import { Directive, ElementRef, HostListener } from '@angular/core';

/**
 * Attribute directive used to stop user entering anything other than a number in an input field
 */

 @Directive({
  selector: '[aaNumberOnly]'
})

export class NumberOnlyDirective {
/**
 * Ensures everything except numeric keys is ignored for the specified element input field
 * @param _el The HTML element on which the attribute directive has been specifiedEnsures
 */
  constructor(private _el: ElementRef) { }

  @HostListener('input', ['$event']) onInputChange(event) {
    const initalValue = this._el.nativeElement.value;
    this._el.nativeElement.value = initalValue.replace(/[^0-9]*/g, '');
    if (initalValue !== this._el.nativeElement.value) {
      event.stopPropagation();
    }
  }
}
