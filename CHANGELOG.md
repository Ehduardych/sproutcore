
CHANGE LOG FOR 1.6
==================

1.6.0.beta.3
------------
* Removed stray debugger statement that broke sc-build


1.6.0.beta.2
------------
* Allow native touch scrolling inside an SC.TemplatePane.
* Add SC.Button template control.
* Created SC.TextField and SC.Checkbox views to eventually replace the *Support mixins.


1.6.0.beta.1
------------
* Bugfixes to synchronization between SproutCore RecordArray/ManyArray/ChildArray and TemplateCollectionView
* Moved forms to experimental framework
* Moved routing into its own framework
* Improved ability to use table elements in Handlebars templates
* CSS and cross-browser fixes for built-in controls
* Significantly cleaned up in-line documentation


CHANGE LOG FOR 1.5
==================

1.5.0
-----

* Fix problem in SC.TextFieldSupport where binding to its value when its layer hasn't been created could potentially start an infinite loop
* Fix range observer support in SC.TreeItemObserver.
* Fixed issue with isVisibleInWindow not getting passed to childViews
* Fix problem with SC.TextFieldView not properly setting input type to password when SC.platform.input.placeholder is true.
* Change SC.View default border color to transparent
* SC.Event.KEY_ENTER updated to SC.Event.KEY_RETURN.  SC.Event.KEY_ENTER is no longer defined.
* Fix bug in SC.ContainerView where it was checking for SC.View instead of SC.CoreView, and add unit test for using SC.TemplateView in SC.ContainerView
* Move some necessary updateLayerLocation code from SC.View to SC.CoreView
* Fix SC.Event mouse handling for Safari 5.0.5, and trust that Apple will continue using extremely huge mouse wheel values
* Fix problem with localizing strings via SC.String.loc, and add unit tests for localizing with multiple parameters.
* Change Foundation String mixin to work standalone with SC.String and mix in mapping to String.prototype. Framework code updated to use SC.String instead of relying on prototype.
* Fixed issue in SC.FormRowView that could cause an infinite loop
* Fixes a bug where bindings would not work when specified in a class definition as an SC.Binding object (as opposed to a property path).
* Fix SC.SAFARI_FOCUS_BEHAVIOR check.
* Don't show experimental apps in welcome list
* Removed mobile references from Buildfile
* Moved Greenhouse and Designer Framework to Experimental
* Remove Docs app since it is worthless
* Remove time.js, update Date validator and tests so that it works with SC.DateTime, and provide warning for backwards compatibility.
* Updates template collection unit test to fail when we were removing child views twice. Also fixes a bug where SC.TemplateCollectionView would not add array observers if the content property was present at initialization time.
* fix firefox 4 transitionEnd case - should be transitionend
* Added back commented out LabelView CSS tests so we know to make them work later
* Remove unused SC.StaticQueue
* Remove CSS tests for LabelView while I figure out how to get document.defaultView.getComputedStyle to return the correct results for framework-level tests.
* Make sure content is defined before trying to access its layer in SC.ScrollView
* Use local image for testing the image view scaling to avoid epic fails
* No longer need to teardown child views when content changes on an SC.TemplateCollectionView.
* Preserve options hash passed to {{#collection}} helper.
* In SC.ScrollView, apply 3D translations even if view does not implement _viewFrameDidChange.
* Split up SC.String and extending String.prototype, change more framework code over to using SC.String.
* Use SC.supplement when mixing into Array.prototype. Create SC.CoreArray which doesn't have SC.Enumerable mixing in to avoid hackiness of old Array handling.
* Added tests for querying nested records by property path
* Added support for quering within SC.Objects or hashes. E.g. "foo.baz = 'bar'". Inspired by an old mailing list post by Thomas Lang.
* Experimental polymorphism: Add ability to pass isPolymorphic in SC.Record.extend hash instead of needing it set it afterwards, with unit test.
* move SC.Request/Response to new framework
* Improved isFixedLayout property plus unit tests.
* jslint cleanup, plus original computeFrameWithParentFrame doesn't use pdim, so don't pass it.
* Fix for potential bug determining frame for non-fixed layout view within static layout parent View.
* Add failing test to illustrate potential bug if a non-fixed layout view is embedded within a static layout view.  Found the bug by accident, but the fix is straightforward so added it (in next commit)
* Require Function.prototype extension in runtime files
* Use Array.isArray in SC.isArray if its available. This is 50% faster when checking arrays and 10% slower when checking objects that aren't arrays, but we're checking arrays 10 times more often than non arrays in SC.isArray, so this is a net win. Unit tests for SC.isArray added.
* Unit test handling of hints on password fields when placeholder is not supported
* Fix hint handling for SC.TextFieldView when isPassword is true
* Fix check for continuouslyUpdatesValue
* Use feature detection instead of browser detection when handling SC.TextFiledView#maxLength
* Deprecate SC.TextFieldView#continuouslyUpdatesValue as its completely broken, use applyImmediately instead.
* Remove SC.TextFieldView#_supportsPlaceHolder and use SC.platform.input.placeholder
* Move SC string localization support to Core Foundation (where it belongs) and small code shuffle in CF
* Reorganize String, Function and Date enhancements in Runtime framework
* Make our String extension handling more sane. SC.CoreString is now SC.String, and Core Foundation additions are now mixed into SC.String. Handlebars loc helper now uses SC.String.loc.
* Add empty SC.ChildRecord object with warning of deprecated to improve 1.4.x backwards compatibility
* Initial work at making framework code prototype-safe. We shouldn't be using helpers attached to native object prototypes in framework code as they can fail on some platforms
* Change instance so "".dasherize to SC.String.dasherize to safeguard against platforms that mix dasherize into String.prototype (I'm looking at you, WebOS)
* Change SC.String functions so they can run standalone as well as when mixed into String.prototype
* More work on documenting Foundation framework
* Add unit tests for Store.loadRecords.
* Ensure that SelectView works with custom views.
* SC.SAFARI_FOCUS_BEHAVIOR is deprecated in favour of SC.FOCUS_ALL_CONTROLS, update docs and unit tests.
* SC.RootResponder now properly checks that responder is defined in makeTouchResponder by accessing properties.
* ContainerView now properly replaces its children. Still need to write a unit test.
* CollectionView should enable or disable the ability to select when isEnabled is true or false.
* Fixed SC.Menu icons in Ace
* Update ImageView so that CSS classes for values are rendered and updated correctly. Unit tests provided.
* CollectionView now calls actions when useToggleSelection and actOnSelect are true
* CollectionView was wiping selections when it was touched but an item wasn't being selected. Behaviour now same as mouse.
* Added toolTip support for imageButtonRenderDelegate
* SC.TabView with tabLocation bottom is positioned correctly.
* Re-render child views if the layer is destroyed then re-created.
* Fix global variable leakage in SC.View layout style code
* Fix problem in CollectionView where using a ListItemView on touch would cause epic fails in the touchEnd event.
* Some styling fixes for Checkbox and Radio icons
* Fixed SC.Query to handle negative numbers
* Now that {{#each}} uses bindings, we have to invoke a run loop in the unit test for it to pass.
* Don't automatically render child views if the view's render method renders them explicitly.
* Added icon examples to TestControls
* Proper location for form render_delegates


1.5.0.rc.2
----------

* Clone itemOptions so that we don't nuke classBindings after the first round trip
* Update SC.ChildArray to use array observers.
* Remove unnecessary invalidation when storeKeys changes in SC.ManyArray.
* When a property observed by a binding is changed outside a run loop, schedule a run loop automatically.
* Remove trailing white space in child array.
* Fixes bug where property chains were being activated even when the associated property had not changed.
* Add support for setting itemViewTemplateName in SC.TemplateCollectionView, plus documentation.
* {{#each}} helper should bind relative to the current context.
* Fix array arithmetic used by SC.TemplateCollectionView when calculating changes.
* Update SC.ManyArray and SC.RecordArray to use array observers.
* Make the test for a simple implementation of SC.Array reflect the API changes.
* Revert changes to SC.Enumerable, move new functionality into SC.Array. Update to use array observer API.
* Update SC.TemplateCollectionView to use new array observer functionality.
* Make sparse arrays support the new Array observer API
* Remove enumerable observers
* Update array controller unit test to use public API when resetting an array.
* Update SC.ArrayController to use array observers.
* Implement array observers. Remove enumerable observers.
* Make our mouse wheel delta detection intelligent about when it sucks. If our browser detection fails and the delta exceeds a specified limit, we readjust so future scrolls aren't Crazy Fast™.
* Initial work on fixing documentation in Foundation framework
* Document SC.browser
* Docs: Markdown-ified Datetime docs
* Docs: Markdown-ified Datastore docs
* Docs: Markdown-ified CoreFoundation docs
* Docs: Markdown-ified Animation docs
* Support the class attribute in {{bindAttr}}.
* SC.TextFieldSupport should notify value change when its loses first responder to support autofill
* Move SproutCore's Handlebars extensions into core_foundation,
* Update testing framework to use new version of qunit, change testing framework to depend on jQuery instead of having its own version
* Remove warning for when a binding connects to an undefined property. This bug has been fixed.
* Ensure that TemplateViews created with an ID by the Handlebars view helper are added to view cache, unit test included
* Add 'datetime/localized' to the Buildfile configs so it doesn't bust for Some Folks. Apologies to Some Folks.
* bindAttr should look up properties relative to its current context, not the view.
* Completed initial audit of Desktop framework documentation
* First stab at fixing the inline documentation in the Desktop framework.
* Separate core DateTime code from localization-specific code as core DateTime code depends only on Runtime
* Unit test and fixes for chained property observers that would cause them to fail if all objects in the chain did not exist at the time the property chain is setup.
* Use touch events for TextField. Required for certain Android platforms
* Fix more unit tests in core_foundation that were trying to delete window properties.
* Internet Explorer does not support deleting properties from the window object.
* Remove trailing commas for IE7 compatibility


1.5.0.rc.1
-----------
* Removed #bindCollection helper. Instead, use {{#collection
  PathTo.Collection contentBinding="MyApp.controller.content"}}
* {{view}} helper looks up views relative to the view, and then the
  global scope
* Built-in helpers and mustaches now automatically update. It is no
  longer necessary to use {{bind}} or {{boundIf}}
* Adds enumerable observers, which allow you to subscribe to mutations
  of an enumerable
* Fixed error reporting when a Handlebars template is unable to find a
  property
* Dependent keys that contain paths now invalidate immediately instead
  of at the end of the run loop, which significantly improves
  performances, especially when combined with @each
* SC.offset offers more reliability than the deprecated SC.viewOffset
* Added SC.getPath(), which is like SC.get() but takes a path instead of
  just a property
* Improved compatibility of using SC.CoreViews (such as SC.TemplateView)
  inside standard SC.Views
* Tear down SC.TemplateCollectionView child views when no longer needed,
  which fixes a memory leak issue
* Integrated new functionality from the Ki framework into the SC.StateChart framework so that they now have feature-parity
* The SC.PickerPane was updated to add removeTarget and removeTarget properties
* Fixed documentation in datastore and view layer
* Refactored and fixed bugs in the way SproutCore handles AutoResizing.
* Updated the test_controls application to reflect AutoResize changes
* Fixed bugs with the selection behavior in lists
* Fixed bugs with the logic that determines when sproutcore applications are ready to begin execution
* Improved performance of layout updates
* Fixed bugs in keyboard behavior of menus
* Made more views utilize render delegates
* Updated unit tests for menus to reflect new keyboard behavior
* Add proper autoresize behavior to buttons
* Fixed frame calculation bugs in lists
* Removed redundant bounds checking in scroll
* Fixed bugs with the localization of titles in segmented views
* Fixes for formView
* Added ability to scale apps so that we can visualize them on the iPhone
* If using StaticLayout in the image, don't use Canvas
* Fixed firstResponder support in text_field
* Fixed responder behavior in editable
* Refactoring for flowed_layout
* Rewrote the existing inline editing code to make it more generic and integrated it with SC.LabelView, SC.InlineTextFieldView and SC.ListItemView
* Added a new SC.SplitView class to the experimental framework which is a re-write of the existing SC.SplitView class but with cleaner code and multi-pane support.
* Introduced a new AlertPane API and backwards compatibility for the existing API. The new API allows us to create an AlertPane by defining a hash of parameters instead of single methods which take 15+ parameters.
* Added the ability to programmatically trigger SC.Ready instead of automatically by jQuery which allows the app developer to decide when his app is ready to run
* Moved render delegates from Ace to base_theme, and render delegates from base to legacy_theme
* Renamed standard_theme to legacy_theme
* Cleaned up old, broken css code in desktop and foundation frameworks
* Updated ImageView documentation
* Small bug fixes throughout
* Added unit tests for new functionality
* Fix failing unit tests


1.5.0.pre.5
-----------
* Support for high resolution screens.
* Support for IE7 base64 images using MHTML
* Initial support for accessibility (WAI-ARIA)
* Improved SC.Logger, allows log recording and different reporting levels like log4j
* Modular loading and whitelisting. 
* Improvements and bug fixes in SC.TemplateView and Handlebars helpers
* Added {{bindAttr}}, {{boundIf}}, and {{collection}} helpers
* Fixes to Ace CSS
* IE7 compatibility fixes
* Numerous bug fixes and minor improvements


1.5.0.pre.4
-----------

* We are beginning to move API that we don't believe will be ready before 1.5
release into the `experimental` framework. If your apps rely on code that is
migrated to experimental, please make sure you include it as a dependency. For
more, please see frameworks/experimental/README.md.
* Support for extending classes after they've been created with the
reopen()/enhance() combo. For more, see: [this
discussion](http://groups.google.com/group/sproutcore-dev/browse_thread/thread/d65ad54d6fddef5d)
	- This change may break existing code if you call sc_super() in your mixins.
	If your app throws exceptions after updating, please see [this post](http://groups.google.com/group/sproutcore-dev/browse_thread/thread/cc6a97e6133cb8cc).
* Added SC.TemplateView and Handlebars. These allow you to specify the content
of your views using templates.
	- {{#view}} helper allows you to define child views
	- {{#bind}} helper allows you to render a property, and automatically update DOM if that
	property ever changes.
	- {{#collection}} helpers allows you to render a simple collection of items
	using templates
	- SC.TextFieldSupport and SC.CheckboxSupport mixins for SC.TemplateViews
	that wrap <input> elements.
* Split SC.View into units of functionality. SC.View remains functionally the
same, but you can now use SC.CoreView, a light-weight subset of SC.View.
* SC.ImageView will use a <canvas> tag on platforms that support it, which
improves performance significantly.
* SC.SegmentedView now creates an overflow menu if there are too many segments
to display.
	- Class names for SC.SegmentedView have been cleaned up. You may need to
	update your CSS if you were theming SC.SegmentedView.
* You can now observe the contents of enumerables using the special `@each`
key.
* Dependent keys can accept property paths. For example, you can say
.property('foo.bar'), and it will be invalidated if the `bar` property of
`foo` changes.
* Deprecated SC.viewportOffset(). Please use SC.offset() instead, which is
more explicit about what it returns.
* SC.browser now detects Android devices.
* SC.device.orientation now works reliably on desktop, iOS, and Android 2.1
and above.
* Experimental support for gyroscope information, if provided by the browser.
* Unit tests for runtime, desktop, foundation, core_foundation, and datastore
are all passing.


CHANGE LOG FOR 1.4
==================

DISCLAIMER: This is a very rough and not comprehensive overview of the 1000+ commits that formed SproutCore 1.4.

MAJOR
-----
* Touch Support Gen 1
* Bug Fixes and Stabilization
* Build tools performance improvements
* Greenhouse (experimental)
* SC.TableView (experimental)


NEW
---
* Implementation of SC.ErrorCatcher.
* Orientation change recognition
* Add all sorts of alt-key goodness to scrollers:
  * alt-click in track scrolls to click
  * alt-click on buttons scrolls by page
  * alt-drag scrolls 1/2 speed.
* CollectionView fast path (experimental)
* SC.Animatable
* Accelerated Layer
* Adding new SC.device object for states such as orientation, online and offline (and moving orientation out from root responder)
* Add application manifest check to html tag of default index.rhtml
* Media framework (experimental)
* Default iPhone loading screen for webapps
* Nested Records (experimental? or functional?)
* SC.DateTime
* SC.StaticContentView
* SC.Border
* Add a task queue to SproutCore, capable of running tasks in the "background"; that is, while idle. (experimental)


MISCELLANEOUS
-------------
* Better IME support
* MainPane now has a 200x200 min app size. This is where you should set the minimum size of your app.
* Move feature detection from SC.browser to SC.platform.
* Desktop framework no longer requires all other frameworks to load
* Improved context menu handling
* Add trigger() method to SC.routes to trigger the current route.
* Improvements to MenuViews
* Add the ability to observe changes on SC.Set at an add/remove level, allowing for efficient filtering, merging, etc.
* Allow configuration of the touch icons and status bar, as well as favicon via Buildfile.
* Add deprecation warning to SC.Scrollable
* Better mouseWheel support
* Added some ARIA tags for accessibility.
* SC.ScrollView / SC.ScrollerView improvements
* Experimental mousewheel momentum support.  Set SC.WHEEL_MOMENTUM to YES.
* Support descending sort in ArrayControllers.
* SC.StaticLayout functionality is now built into SC.View
* Allow panes the chance to handle user events.
* Fixes/improvements to PopupButton
* Make inline text editor inherit escapeHTML from the list item view
* Added domCSSPrefix to SC.platform
* Make views update their layer's layerId if their layerId changes.
* Adding maxlength property to textfield view
* Added inflector functions to SC.String: singularize() and pluralize()  
* Adding mousewheel support to textareas.
* Adding HTML5 spellCheck support for textfields. It works with the latest versions of Firefox, Sproutcore, Chrome
* Adding lastObject() method to SC.Enumerable
* Allow SC.outlet to specify a different root.
* Improvements to drag/drop
* Improvements to SC.UserDefaults
* Switch from XHTML -> HTML5.
* Update SelectButtonView to use target/action instead of deprecated function calls.
* Invoke button actions after a delay if triggered by keyboard shortcuts.
* Make PopupButtonView and SelectButtonView click and hold delay a constant. Also lowered default value.
* Use SC.Enumerable's sortProperty to sort objects so that this works on any SC.Enumerable not just native arrays.
* SC.Record: Add in a the new concept of 'readOnlyAttributes' to complement 'attributes'.
* New type of SC.PickerPane: PICKER_MENU_POINTER - It's a menu but position like picker pointer
* Add a willRemoveAllChildren to SC.CollectionView.
* Added max() and min() to SC.Array
* Added isDescendantOf method to SC.View
* Added acceptFirstResponder code to radio and checkbox button.
* Add a constant for the default separator height, too.
* use SC.WELL_CONTAINER_PADDING for well and change default value to 15
* Initial support for re-using views in collections
* Push an extra div into the scrollView so that it's possible to style the corner differently.
* Moved all of the standard theme scroller metrics into SproutCore as default values.
* Adding themes to segmented view
* Changing tabView so you can set the height of the tabs with a global variable
* Added provision for Enabling/Disabling menu items in SelectButtonView
* AlertPane: Esc triggers cancel button / enter triggers default button
* SC.Query: 'orderBy' can now optionally be a comparison function. In this case, the specified function will be passed the two records directly, rather than the typical method of operating on specific properties.  This can be useful for complicated comparisons that cannot be expressed by the simpler method.   
* Add option to only allow focus tabbing among webapp controls.(No jumping to address bar
* pushRetrieve, pushDestroy and pushError now return storeKey on success instead of YES
* If there is a list item being edited, commit the changes if the list is scrolled.
* New Validator for positive integers and also accepts a default value
* Make sure we always have a root responder.
* Taught toFormattedString to handle characters %h (unpadded 24-hour time, 1-24) and %i (unpadded 12-hour time, 1-12).
* FocusRings for SC.ButtonView
* Adding a handy escapeForRegExp method to String
* Alignment support for SC.SegmentedView
* allowing text fields to only apply changes on blur via applyImmediately: NO
* Added a property to enable/disable textfield tabbing.
* Removed mobile framework as it was unnecessary
* Update all encodings to be valid UTF-8
* We now force parentViewDidResize. It is no longer optional.
* Only add 'px' units to layout values that are numbers. Strings will be unchanged.
* 'layerLocationNeedsUpdate' is not set until updates are completed.
* If a pane receives a tab key press, try to find the next eligible view in the view hierarchy and assign it first responder.
* In collection view, check if the item is loaded or not before advancing to it.
* SelectButtonView should by default highlight whatever item is set to its value property.
* SC.Request: Added 'proper' async() function
* Changed disclosure from using a label tag to using span
* add debug() support to SC.Logger
* Added the shouldInheritCursor property & documentation to SC.View.  Defaults to YES.
* ResponderContext is now a mixin included by SC.Pane and SC.Application.
* TextFieldView: add support for escapeHTML
* Renamed isEnabledObserver to reduce the likelihood of naming collisions.
* Move Date.now() into runtime, and only implement if the browser does not.
* do not append font-weight style with px
* Disable other mouse events while dealing with inputs.



BUG FIXES
---------
* XSS security improvements
* Fixed a bug with listItem views not always being removed properly
* Miscellaneous code cleanup, optimizations and fixes
* Fix for memory leak in SC.Response
* Fixed issue with SC.ManyArray not notifying inverse attributes of correct records that got removed in SC.ManyArray#replace, with tests.
* TextField hint was not updating for browsers that support placeholder
* Fix SC.Object so it handles both local and non-local property paths at the same time.
* Fixed SC.Binding.disconnect()
* Initialize the value of the select field view to the value of the first element if there is no emptyName and the value hasn't been previously set.
* Fixed RenderContext to properly handle styles starting with a dash
* Change the value of the textfield on keyDown to reflect key repetitions.
* Ignore moveRight and moveLeft events if the user has a control or meta key held down. Otherwise, we may inadvertently block browser keyboard shortcuts.
* Destroy the layer before removing from parent , otherwise the view will leak
* Fixes to SC.SegmentedView.
* Fixed checkbox/righticon/disclosure states in SC.ListItemView
* RootResponder's performKeyEquivalent should check the menupane before the keypane.
* Fixed broken useToggleSelection property.
* Correctly trigger the document's 'ready' event
* SC.LabelView was lacking a default implementation of inlineEditorShouldBeginEditing(), so by default it would never switch to editable mode when 'isEditable' == true.
* Fix for bug in SC.Record.normalize().  It would try to normalize a null child record reference.
* SC.Event.special.mouseover didn't exist, changing it to mouseenter fixes the mouseenter event
* RecordAttribute: Allow null dates
* Checking / Unchecking checkboxes or clicking in empty space was not removing focus from in-focus form fields
* Fixing before ondeactivate in textfield as it is not letting textfields within iframes get focus
* Invalidate the verticalScrollOffset and horizontalScrollOffset with -1 instead of 0, because those are actually valid values.
* Reset the click count if clicks occur too far away from one another
* Make SC.RecordAttribute respect isEditable
* SC.SelectButton should accept first responder only if it is enabled.
* Prevent scrollbars from being shown when PickerPane is opened.




BROWSER
-------
* XHR requests now work with Opera
* IE7 fixes
* Fixed problem with poor security management in FF4
* Fix for window focus events on IE.
* Fixed issue with underscore characters not appearing in IE text fields.
* Adding extra validation to avoid incorrect appearance of hint when deleting all text while using firefox
* Fix the default # added in FF and IE when using routes
* SC.Pane should not call sendAction from its sendEvent implementation.
* Fixing IE8 selection woes and removing a lot of legacy cross-browser code
* Resolve a bug where other panes would disappear if a menu pane was opened (IE7 only).
* Fix for SC.button on IE7, now it calculates the label with once is appended to the document
* SC.TextFieldView: Default hint as empty string to avoid IE displaying null in the text fields

