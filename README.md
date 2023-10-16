# myprojects
document.addEventListener("DOMContentLoaded", function() {
    const form = document.getElementById("register");
    const fname = document.getElementById("fname");
    const lname = document.getElementById("lname");
    const regno = document.getElementById("regno");
    const gender = document.querySelectorAll('input[name="gender"]');
    const dob = document.getElementById("datemax");
    const department = document.getElementById("department");
    const pno = document.getElementById("pno");
    const email = document.getElementById("email");
    const address = document.querySelector('textarea');

    const errorFname = document.getElementById("fnameerror");
    const errorLname = document.getElementById("lnameerror");
    const errorRegno = document.getElementById("regnoerror");
    const errorGender = document.getElementById("gendererror");
    const errorDob = document.getElementById("doberror");
    const errorDept = document.getElementById("depterror");
    const errorPno = document.getElementById("pnoerror");
    const errorEmail = document.getElementById("emailerror");
    const errorAddress = document.getElementById("addresserror");

    form.addEventListener("submit", function(e) {
        let isValid = true;

        if (fname.value === "") {
            errorFname.textContent = "First Name is required";
            isValid = false;
        } else {
            errorFname.textContent = "";
        }

        if (lname.value === "") {
            errorLname.textContent = "Last Name is required";
            isValid = false;
        } else {
            errorLname.textContent = "";
        }

        if (regno.value === "" || isNaN(regno.value)) {
            errorRegno.textContent = "Valid Registration number is required";
            isValid = false;
        } else {
            errorRegno.textContent = "";
        }

        let genderSelected = false;
        for (let i = 0; i < gender.length; i++) {
            if (gender[i].checked) {
                genderSelected = true;
                break;
            }
        }

        if (!genderSelected) {
            errorGender.textContent = "Gender is required";
            isValid = false;
        } else {
            errorGender.textContent = "";
        }

        if (dob.value === "") {
            errorDob.textContent = "Date of Birth is required";
            isValid = false;
        } else {
            errorDob.textContent = "";
        }

        if (department.value === "computer") {
            errorDept.textContent = "Department is required";
            isValid = false;
        } else {
            errorDept.textContent = "";
        }

        if (pno.value === "" || isNaN(pno.value)) {
            errorPno.textContent = "Valid Phone Number is required";
            isValid = false;
        } else {
            errorPno.textContent = "";
        }

        if (email.value === "" || !isValidEmail(email.value)) {
            errorEmail.textContent = "Valid Email is required";
            isValid = false;
        } else {
            errorEmail.textContent = "";
        }

        if (address.value === "") {
            errorAddress.textContent = "Address is required";
            isValid = false;
        } else {
            errorAddress.textContent = "";
        }

        if (!isValid) {
            e.preventDefault();
        }
    });

    function isValidEmail(email) {
        const emailRegex =
