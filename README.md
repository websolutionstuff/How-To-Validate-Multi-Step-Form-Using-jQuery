# How To Validate Multi Step Form Using jQuery

In this article, we will see how to validate multi step form wizard using jquery. Here, we will learn to validate the multi step form using jquery. First, we create the multi step form using bootstrap. Also, in this example, we are not using any jquery plugin for multi step form wizard.

So, let's see jquery multi step form with validation, how to create multi step form, multi step form wizard with jquery validation, bootstrap 4 multi step form wizard with validation, multi step form bootstrap 5, and jQuery multi step form with validation and next previous navigation.

**Add HTML:**

```
<html lang="en">
</head>
<link href="https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap" rel="stylesheet">
</head>
<body>  
    <div class="main">
      <h3>How To Validate Multi Step Form Using jQuery - Websolutionstuff</h3>
        <form id="multistep_form">
            <!-- progressbar -->
            <ul id="progress_header">
                <li class="active"></li>
                <li></li>
                <li></li>
            </ul>
            <!-- Step 01 -->
            <div class="multistep-box">
                <div class="title-box">
                    <h2>Create your account</h2>
                </div>
                <p>
                    <input type="text" name="email" placeholder="Email" id="email">
                    <span id="error-email"></span>
                </p>
                <p>
                    <input type="password" name="pass" placeholder="Password" id="pass">
                    <span id="error-pass"></span>
                </p>
                <p>
                    <input type="password" name="cpass" placeholder="Confirm Password" id="cpass">
                    <span id="error-cpass"></span>
                </p>
                <p class="nxt-prev-button"><input type="button" name="next" class="fs_next_btn action-button" value="Next" /></p>
            </div>
            <!-- Step 02 -->
            <div class="multistep-box">
                <div class="title-box">
                    <h2>Social Profiles</h2>
                </div>
                <p>
                    <input type="text" name="twitter" placeholder="Twitter" id="twitter">
                    <span id="error-twitter"></span>
                </p>
                <p>
                    <input type="text" name="facebook" placeholder="Facebook" id="facebook">
                    <span id="error-facebook"></span>
                </p>
                <p>
                    <input type="text" name="linkedin" placeholder="Linkedin" id="linkedin">
                    <span id="error-linkedin"></span>
                </p>
                <p class="nxt-prev-button">
                    <input type="button" name="previous" class="previous action-button" value="Previous" />
                    <input type="button" name="next" class="ss_next_btn action-button" value="Next" />
                </p>
            </div>
            <!-- Step 03 -->
            <div class="multistep-box">
                <div class="title-box">
                    <h2>Personal Details</h2>
                </div>
                <p>
                    <input type="text" name="fname" placeholder="First Name" id="fname">
                    <span id="error-fname"></span>
                </p>
                <p>
                    <input type="text" name="lname" placeholder="Last Name" id="lname">
                    <span id="error-lname"></span>
                </p>
                <p>
                    <input type="text" name="phone" placeholder="Phone" id="phone">
                    <span id="error-phone"></span>
                </p>
                <p>
                    <textarea name="address" placeholder="Address" id="address"></textarea>
                    <span id="error-address"></span>
                </p>
                <p class="nxt-prev-button"><input type="button" name="previous" class="previous action-button" value="Previous" />
                    <input type="submit" name="submit" class="submit_btn ts_next_btn action-button" value="Submit" />
                </p>
            </div>
        </form>
        <h1>You are successfully logged in</h1>
    </div>
    <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-easing/1.4.0/jquery.easing.js" type="text/javascript"></script>
</body>
</html>
```

**Add CSS:**

```
body {
    display: inline-block;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    background-image: url("https://img1.akspic.com/image/80377-gadget-numeric_keypad-input_device-electronic_device-space_bar-3840x2160.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    position: relative;
    margin: 0;
    font-weight: 400;
    font-family: 'Roboto', sans-serif;
}
body:before {
    content: "";
    display: block;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
}
.main {
    position: absolute;
    left: 0;
    right: 0;
    top: 30px;
    margin: 0 auto;
    height: 515px;
}
input:-internal-autofill-selected {
    background-color: #fff !important;
}
#multistep_form {
    width: 550px;
    margin: 0 auto;
    text-align: center;
    position: relative;
    height: 100%;
    z-index: 999;
    opacity: 1; 
    visibility: visible; 
}
/*progress header*/
#progress_header {
    overflow: hidden;
    margin: 0 auto 30px;
    padding: 0;
}
#progress_header li {
    list-style-type: none;
    width: 33.33%;
    float: left;
    position: relative;
    font-size: 16px;
    font-weight: bold;
    font-family: monospace;
    color: #fff;
    text-transform: uppercase;
}
#progress_header li:after {
    width: 35px;
    line-height: 35px;
    display: block;
    font-size: 22px;
    color: #888;
    font-family: monospace;
    background-color: #fff;
    border-radius: 100px;
    margin: 0 auto;
    background-repeat: no-repeat;
    font-family: 'Roboto', sans-serif;
}
#progress_header li:nth-child(1):after {
    content: "1";
}
#progress_header li:nth-child(2):after {
    content: "2";
}
#progress_header li:nth-child(3):after {
    content: "3";
}
#progress_header li:before {
    content: '';
    width: 100%;
    height: 5px;
    background: #fff;
    position: absolute;
    left: -50%;
    top: 50%;
    z-index: -1;
}
#progress_header li:first-child:before {
    content: none;
}
#progress_header li.active:before, 
#progress_header li.active:after {
    background-image: linear-gradient(to right top, #35e8c3, #36edbb, #3df2b2, #4af7a7, #59fb9b) !important;
    color: #fff !important;
    transition: all 0.5s;
}
/*title*/
.title-box {
    width: 100%;
    margin: 0 0 30px 0;
}
.title-box h2 {
    font-size: 22px;
    text-transform: uppercase;
    color: #2C3E50;
    margin: 0;
    font-family: cursive;
    display: inline-block;
    position: relative;
    padding: 0 0 10px 0;
    font-family: 'Roboto', sans-serif;
}
.title-box h2:before {
    content: "";
    background: #6ddc8b;
    width: 70px;
    height: 2px;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    margin: 0 auto;
    display: block;
}
.title-box h2:after {
    content: "";
    background: #6ddc8b;
    width: 50px;
    height: 2px;
    position: absolute;
    bottom: -5px;
    left: 0;
    right: 0;
    margin: 0 auto;
    display: block;
}
/*Input and Button*/
.multistep-box {
    background: white;
    border: 0 none;
    border-radius: 3px;
    box-shadow: 1px 1px 55px 3px rgba(255, 255, 255, 0.4);
    padding: 30px 30px;
    box-sizing: border-box;
    width: 80%;
    margin: 0 10%;
    position: absolute;
}
.multistep-box:not(:first-of-type) {
    display: none;
}
.multistep-box p {
    margin: 0 0 12px 0;
    text-align: left;
}
.multistep-box span {
    font-size: 12px;
    color: #FF0000;
}
input, textarea {
    padding: 15px;
    border: 1px solid #ccc;
    border-radius: 3px;
    margin: 0;
    width: 100%;
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
    color: #2C3E50;
    font-size: 13px;
    transition: all 0.5s;
    outline: none;
}
input:focus, textarea:focus {
    box-shadow: inset 0px 0px 50px 2px rgb(0,0,0,0.1);
}
input.box_error, textarea.box_error {
    border-color: #FF0000;
    box-shadow: inset 0px 0px 50px 2px rgb(255,0,0,0.1);
}
input.box_error:focus, textarea.box_error:focus {
    box-shadow: inset 0px 0px 50px 2px rgb(255,0,0,0.1);
}
p.nxt-prev-button {
    margin: 25px 0 0 0;
    text-align: center;
}
.action-button {
    width: 100px;
    font-weight: bold;
    color: white;
    border: 0 none;
    border-radius: 1px;
    cursor: pointer;
    padding: 10px 5px;
    margin: 0 5px;
    background-image: linear-gradient(to right top, #35e8c3, #36edbb, #3df2b2, #4af7a7, #59fb9b);
    transition: all 0.5s;
}
.action-button:hover, 
.action-button:focus {
    box-shadow: 0 0 0 2px white, 0 0 0 3px #6ce199;
}
.form_submited #multistep_form {
    opacity: 0; 
    visibility: hidden; 
}
.form_submited h1 {
    -webkit-background-clip: text;
    transform: translate(0%, 0%);
    -webkit-transform: translate(0%, 0%);
    transition: all 0.3s ease;
    opacity: 1;
    visibility: visible;
}
h1 {
    margin: 0;
    text-align: center;
    font-size: 90px;
    background-image: linear-gradient(to right top, #35e8c3, #36edbb, #3df2b2, #4af7a7, #59fb9b) !important;
    background-image: linear-gradient(to right top, #35e8c3, #36edbb, #3df2b2, #4af7a7, #59fb9b) !important;
    color: transparent;
    -webkit-background-clip: text;
    -webkit-background-clip: text;
    transform: translate(0%, -80%);
    -webkit-transform: translate(0%, -80%);
    transition: all 0.3s ease;
    opacity: 0;
    visibility: hidden;
    position: absolute;
    left: 0;
    right: 0;
    margin: 0 auto;
    text-align: center;
    top: 50%;
}
h3{
  color:#fff;
  text-align:center;
  margin-bottom:20px;
}
```

**Add jQuery:**

```
var current_slide, next_slide, previous_slide;
var left, opacity, scale;
var animation;

var error = false;

// email validation
$("#email").keyup(function() {
    var emailReg = /^([\w-\.]+@([\w-]+\.)+[\w-]{2,4})?$/;
    if (!emailReg.test($("#email").val())) {
        $("#error-email").text('Please enter an Email addres.');
        $("#email").addClass("box_error");
        error = true;
    } else {
        $("#error-email").text('');
        error = false;
        $("#email").removeClass("box_error");
    }
});
// password validation
$("#pass").keyup(function() {
    var pass = $("#pass").val();
    var cpass = $("#cpass").val();

    if (pass != '') {
        $("#error-pass").text('');
        error = false;
        $("#pass").removeClass("box_error");
    }
    if (pass != cpass && cpass != '') {
        $("#error-cpass").text('Password and Confirm Password is not matched.');
        error = true;
    } else {
        $("#error-cpass").text('');
        error = false;
    }
});
// confirm password validation
$("#cpass").keyup(function() {
    var pass = $("#pass").val();
    var cpass = $("#cpass").val();

    if (pass != cpass) {
        $("#error-cpass").text('Please enter the same Password as above.');
        $("#cpass").addClass("box_error");
        error = true;
    } else {
        $("#error-cpass").text('');
        error = false;
        $("#cpass").removeClass("box_error");
    }
});
// twitter
$("#twitter").keyup(function() {
    var twitterReg = /https?:\/\/twitter\.com\/(#!\/)?[a-z0-9_]+$/;
    if (!twitterReg.test($("#twitter").val())) {
        $("#error-twitter").text('Twitter link is not valid.');
        $("#twitter").addClass("box_error");
        error = true;
    } else {
        $("#error-twitter").text('');
        error = false;
        $("#twitter").removeClass("box_error");
    }
});
// facebook
$("#facebook").keyup(function() {
    var facebookReg = /^(https?:\/\/)?(www\.)?facebook.com\/[a-zA-Z0-9(\.\?)?]/;
    if (!facebookReg.test($("#facebook").val())) {
        $("#error-facebook").text('Facebook link is not valid.');
        $("#facebook").addClass("box_error");
        error = true;
    } else {
        $("#error-facebook").text('');
        error = false;
        $("#facebook").removeClass("box_error");
    }
});
// linkedin
$("#linkedin").keyup(function() {
    var linkedinReg = /(ftp|http|https):\/\/?(?:www\.)?linkedin.com(\w+:{0,1}\w*@)?(\S+)(:([0-9])+)?(\/|\/([\w#!:.?+=&%@!\-\/]))?/;
    if (!linkedinReg.test($("#linkedin").val())) {
        $("#error-linkedin").text('Linkedin link is not valid.');
        $("#linkedin").addClass("box_error");
        error = true;
    } else {
        $("#error-linkedin").text('');
        error = false;
        $("#linkedin").removeClass("box_error");
    }
});
// first name
$("#fname").keyup(function() {
    var fname = $("#fname").val();
    if (fname == '') {
        $("#error-fname").text('Enter your First name.');
        $("#fname").addClass("box_error");
        error = true;
    } else {
        $("#error-fname").text('');
        error = false;
    }
    if ((fname.length <= 2) || (fname.length > 20)) {
        $("#error-fname").text("User length must be between 2 and 20 Characters.");
        $("#fname").addClass("box_error");
        error = true;
    }
    if (!isNaN(fname)) {
        $("#error-fname").text("Only Characters are allowed.");
        $("#fname").addClass("box_error");
        error = true;
    } else {
        $("#fname").removeClass("box_error");
    }
});
// last name
$("#lname").keyup(function() {
    var lname = $("#lname").val();
    if (lname != lname) {
        $("#error-lname").text('Enter your Last name.');
        $("#lname").addClass("box_error");
        error = true;
    } else {
        $("#error-lname").text('');
        error = false;
    }
    if ((lname.length <= 2) || (lname.length > 20)) {
        $("#error-lname").text("User length must be between 2 and 20 Characters.");
        $("#lname").addClass("box_error");
        error = true;
    }
    if (!isNaN(lname)) {
        $("#error-lname").text("Only Characters are allowed.");
        $("#lname").addClass("box_error");
        error = true;
    } else {
        $("#lname").removeClass("box_error");
    }
});
// phone
$("#phone").keyup(function() {
    var phone = $("#phone").val();
    if (phone != phone) {
        $("#error-phone").text('Enter your Phone number.');
        $("#phone").addClass("box_error");
        error = true;
    } else {
        $("#error-phone").text('');
        error = false;
    }
    if (phone.length != 10) {
        $("#error-phone").text("Mobile number must be of 10 Digits only.");
        $("#phone").addClass("box_error");
        error = true;
    } else {
        $("#phone").removeClass("box_error");
    }
});
// address
$("#address").keyup(function() {
    var address = $("#address").val();
    if (address != address) {
        $("#error-address").text('Enter your Address.');
        $("#address").addClass("box_error");
        error = true;
    } else {
        $("#error-address").text('');
        error = false;
        $("#address").removeClass("box_error");
    }
});

// first step validation
$(".fs_next_btn").click(function() {
    // email
    if ($("#email").val() == '') {
        $("#error-email").text('Please enter an email address.');
        $("#email").addClass("box_error");
        error = true;
    } else {
        var emailReg = /^([\w-\.]+@([\w-]+\.)+[\w-]{2,4})?$/;
        if (!emailReg.test($("#email").val())) {
            $("#error-email").text('Please insert a valid email address.');
            error = true;
        } else {
            $("#error-email").text('');
            $("#email").removeClass("box_error");
        }
    }
    // password
    if ($("#pass").val() == '') {
        $("#error-pass").text('Please enter a password.');
        $("#pass").addClass("box_error");
        error = true;
    }
    if ($("#cpass").val() == '') {
        $("#error-cpass").text('Please enter a Confirm password.');
        $("#cpass").addClass("box_error");
        error = true;
    } else {
        var pass = $("#pass").val();
        var cpass = $("#cpass").val();

        if (pass != cpass) {
            $("#error-cpass").text('Please enter the same password as above.');
            error = true;
        } else {
            $("#error-cpass").text('');
            $("#pass").removeClass("box_error");
            $("#cpass").removeClass("box_error");
        }
    }
    // animation
    if (!error) {
        if (animation) return false;
        animation = true;

        current_slide = $(this).parent().parent();
        next_slide = $(this).parent().parent().next();

        $("#progress_header li").eq($(".multistep-box").index(next_slide)).addClass("active");

        next_slide.show();
        current_slide.animate({
            opacity: 0
        }, {
            step: function(now, mx) {
                scale = 1 - (1 - now) * 0.2;
                left = (now * 50) + "%";
                opacity = 1 - now;
                current_slide.css({
                    'transform': 'scale(' + scale + ')'
                });
                next_slide.css({
                    'left': left,
                    'opacity': opacity
                });
            },
            duration: 800,
            complete: function() {
                current_slide.hide();
                animation = false;
            },
            easing: 'easeInOutBack'
        });
    }
});
// second step validation
$(".ss_next_btn").click(function() {
    // twitter
    if ($("#twitter").val() == '') {
        $("#error-twitter").text('twitter link is required.');
        $("#twitter").addClass("box_error");
        error = true;
    } else {
        var twitterReg = /https?:\/\/twitter\.com\/(#!\/)?[a-z0-9_]+$/;
        if (!twitterReg.test($("#twitter").val())) {
            $("#error-twitter").text('Twitter link is not valid.');
            error = true;
        } else {
            $("#error-twitter").text('');
            $("#twitter").removeClass("box_error");
        }
    }
    // facebook
    if ($("#facebook").val() == '') {
        $("#error-facebook").text('Facebook link is required.');
        $("#facebook").addClass("box_error");
        error = true;
    } else {
        var facebookReg = /^(https?:\/\/)?(www\.)?facebook.com\/[a-zA-Z0-9(\.\?)?]/;
        if (!facebookReg.test($("#facebook").val())) {
            $("#error-facebook").text('Facebook link is not valid.');
            error = true;
            $("#facebook").addClass("box_error");
        } else {
            $("#error-facebook").text('');
        }
    }
    // linkedin
    if ($("#linkedin").val() == '') {
        $("#error-linkedin").text('Linkedin link is required.');
        $("#linkedin").addClass("box_error");
        error = true;
    } else {
        var linkedinReg = /(ftp|http|https):\/\/?(?:www\.)?linkedin.com(\w+:{0,1}\w*@)?(\S+)(:([0-9])+)?(\/|\/([\w#!:.?+=&%@!\-\/]))?/;
        if (!linkedinReg.test($("#linkedin").val())) {
            $("#error-linkedin").text('Linkedin link is not valid.');
            error = true;
        } else {
            $("#error-linkedin").text('');
            $("#linkedin").removeClass("box_error");
        }
    }

    if (!error) {
        if (animation) return false;
        animation = true;

        current_slide = $(this).parent().parent();
        next_slide = $(this).parent().parent().next();

        $("#progress_header li").eq($(".multistep-box").index(next_slide)).addClass("active");

        next_slide.show();
        current_slide.animate({
            opacity: 0
        }, {
            step: function(now, mx) {
                scale = 1 - (1 - now) * 0.2;
                left = (now * 50) + "%";
                opacity = 1 - now;
                current_slide.css({
                    'transform': 'scale(' + scale + ')'
                });
                next_slide.css({
                    'left': left,
                    'opacity': opacity
                });
            },
            duration: 800,
            complete: function() {
                current_slide.hide();
                animation = false;
            },
            easing: 'easeInOutBack'
        });
    }

});

// third step validation
$(".ts_next_btn").click(function() {
    // first name
    if ($("#fname").val() == '') {
        $("#error-fname").text('Enter your First name.');
        $("#fname").addClass("box_error");
        error = true;
    } else {
        var fname = $("#fname").val();
        if (fname != fname) {
            $("#error-fname").text('First name is required.');
            error = true;
        } else {
            $("#error-fname").text('');
            error = false;
            $("#fname").removeClass("box_error");
        }
        if ((fname.length <= 2) || (fname.length > 20)) {
            $("#error-fname").text("User length must be between 2 and 20 Characters.");
            error = true;
        }
        if (!isNaN(fname)) {
            $("#error-fname").text("Only Characters are allowed.");
            error = true;
        } else {
            $("#fname").removeClass("box_error");
        }
    }
    // last name
    if ($("#lname").val() == '') {
        $("#error-lname").text('Enter your Last name.');
        $("#lname").addClass("box_error");
        error = true;
    } else {
        var lname = $("#lname").val();
        if (lname != lname) {
            $("#error-lname").text('Last name is required.');
            error = true;
        } else {
            $("#error-lname").text('');
            error = false;
        }
        if ((lname.length <= 2) || (lname.length > 20)) {
            $("#error-lname").text("User length must be between 2 and 20 Characters.");
            error = true;
        } 
        if (!isNaN(lname)) {
            $("#error-lname").text("Only Characters are allowed.");
            error = true;
        } else {
            $("#lname").removeClass("box_error");
        }
    }
    // phone
    if ($("#phone").val() == '') {
        $("#error-phone").text('Enter your Phone number.');
        $("#phone").addClass("box_error");
        error = true;
    } else {
        var phone = $("#phone").val();
        if (phone != phone) {
            $("#error-phone").text('Phone number is required.');
            error = true;
        } else {
            $("#error-phone").text('');
            error = false;
        }
        if (phone.length != 10) {
            $("#error-phone").text("Mobile number must be of 10 Digits only.");
            error = true;
        } else {
            $("#phone").removeClass("box_error");
        }
    }
    // address
    if ($("#address").val() == '') {
        $("#error-address").text('Enter your Address.');
        $("#address").addClass("box_error");
        error = true;
    } else {
        var address = $("#address").val();
        if (address != address) {
            $("#error-address").text('Address is required.');
            error = true;
        } else {
            $("#error-address").text('');
            $("#address").removeClass("box_error");
            error = false;
        }
    }

    if (!error) {
        if (animation) return false;
        animation = true;

        current_slide = $(this).parent().parent();
        next_slide = $(this).parent().parent().next();

        $("#progress_header li").eq($(".multistep-box").index(next_slide)).addClass("active");

        next_slide.show();
        current_slide.animate({
            opacity: 0
        }, {
            step: function(now, mx) {
                scale = 1 - (1 - now) * 0.2;
                left = (now * 50) + "%";
                opacity = 1 - now;
                current_slide.css({
                    'transform': 'scale(' + scale + ')'
                });
                next_slide.css({
                    'left': left,
                    'opacity': opacity
                });
            },
            duration: 800,
            complete: function() {
                current_slide.hide();
                animation = false;
            },
            easing: 'easeInOutBack'
        });
    }
});
// previous
$(".previous").click(function() {
    if (animation) return false;
    animation = true;

    current_slide = $(this).parent().parent();
    previous_slide = $(this).parent().parent().prev();

    $("#progress_header li").eq($(".multistep-box").index(current_slide)).removeClass("active");

    previous_slide.show();
    current_slide.animate({
        opacity: 0
    }, {
        step: function(now, mx) {
            scale = 0.8 + (1 - now) * 0.2;
            left = ((1 - now) * 50) + "%";
            opacity = 1 - now;
            current_slide.css({
                'left': left
            });
            previous_slide.css({
                'transform': 'scale(' + scale + ')',
                'opacity': opacity
            });
        },
        duration: 800,
        complete: function() {
            current_slide.hide();
            animation = false;
        },
        easing: 'easeInOutBack'
    });
});

$(".submit_btn").click(function() {
    if (!error){
        $(".main").addClass("form_submited");
    }
    return false;
})
```

Output:

![how_to_validate_multi_step_form_using_jquery_output](https://user-images.githubusercontent.com/67193237/208668046-94245375-6fe4-4994-a733-a9bb0014dfed.jpg)

---

**You might also like:**

- **[Read Also: jQuery Datatable Hide/Show Column Based On Condition](https://websolutionstuff.com/post/jquery-datatable-hide-show-column-based-on-condition)**
- **[Read Also: Multi Step Form Example In Laravel](https://websolutionstuff.com/post/multi-step-form-example-in-laravel)**
- **[Read Also: Laravel 9 Form Collective Example](https://websolutionstuff.com/post/laravel-9-form-collective-example)**
- **[Read Also: Laravel 9 Form Class Not Found](https://websolutionstuff.com/post/laravel-9-form-class-not-found)**
- **[Read Also: Multi Step Form Wizard jQuery Validation](https://websolutionstuff.com/post/multi-step-form-wizard-jquery-validation)**
